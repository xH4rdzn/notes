___
- Como tipamos o nosso `prismaUsersRepository`, como `any`, ele não conhece diretamente quais métodos temos, mas ele precisa saber quais dados ele recebe e devolve.
- Para isso na pasta `repositories`, vamos criar o arquivo `usersRepository.ts`, e dentro dele vamos fazer o seguinte:
```Ts
import { Prisma, User } from '@prisma/client'
export interface UsersRepository {
	create(data: Prisma.UserCreateInput): Promise<User>
}
```
- Agora no nosso caso de uso voltamos e passamos a tipagem para ele:
```ts
import { UsersRepository } from '@/repositories/usersRepository'
export class RegisterUseCase {
	

	constructor(private usersRepository: UsersRepository) {}

	async execute({name, email, password}:) {
		await this.usersRepository.create({
			name,
			email,
			password
		})
	}
}
```
- Agora no `prismaUsersRepository`implementamos o `UsersRepository`, para que obrigue a ter os métodos que são descritos na interface:
```TS
import { prisma } from '@/lib/prisma'
import { Prisma } from '@prisma/client'
import { UsersRepository } from '../usersRepository'

export class PrismaUsersRepository implements UsersRepository {
	async create(data: Prisma.UserCreateInput) {
		const user = await prisma.user.create({
			data,
		})

		return user
	}
}
```
- Para deixar organizado dentro da pasta `repositories`vamos criar uma pasta com o nome de `prisma`e dentro dessa pasta vamos por todos os repositórios específicos do prisma nessa pasta;
- *SEMPRE QUE FORMOS IMPLEMENTAR UM NOVO MÉTODO, COMEÇAMOS PELA INTERFACE*
- Nesse caso vamos criar um método para buscar um usuário pelo *email*, então voltamos a interface e fazemos sua implementação:
```ts
import { Prisma, User } from '@prisma/client'


export interface UsersRepository {
	findByEmail(email: string): Promise<User | null>
		
	create(data: Prisma.UserCreateInput): Promise<User>
}
```
- Agora implementamos esse método no nosso repositório.
```ts
import { prisma } from '@/lib/prisma'
import { Prisma } from '@prisma/client'
import { UsersRepository } from '../usersRepository'

export class PrismaUsersRepository implements UsersRepository {

	async findByEmail(email: string) {
		const user = await prisma.user.findUnique({
			where: {
				email,
			}
		})

		return user
	}

	async create(data: Prisma.UserCreateInput) {
		const user = await prisma.user.create({
			data,
		})

		return user
	}
}
```
- Agora voltamos ao nosso caso de uso e alteramos:
```ts
import { UsersRepository } from '@/repositories/usersRepository'

import { hash } from 'bcryptjs'

export class RegisterUseCase {
	

	constructor(private usersRepository: any) {
		this.usersRepository
	}

	async execute({name, email, password}:) {
		const passwordHashed = await hash(password, 6)
		const userWithSameEmail = await this.usersRepository.findByEmail(email)

		if(userWithSameEmail) {
			throw new Error('E-mail already exists.')
		}
	
		await this.usersRepository.create({
			name,
			email,
			password
		})
	}
}
```