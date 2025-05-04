___
- Normalmente, cada regra de negócio da nossa aplicação vai exigir pelo menos um teste.
- Voltando ao arquivo de `register.spec.ts`, podemos criar da seguinte maneira:
```ts
import { expect, describe, it } from 'vitest'


describe('Register Use Case', () => {
	it('should hash user password upon registration', () => {
		const prismaUsersRepository = new PrismaUsersRepository()
		const registerUseCase = new RegisterUseCase(prismaUsersRepository)
	})

		await registerUseCase.execute({
			name: 'John Doe',
			email: 'johndoe@email.com',
			password: '123456'
		})
})
```
- Porém precisamos devolver o nosso `user`, para isso voltamos ao nosso `registerUseCase.ts` e alteramos para ele devolver o `user`, da seguinte maneira:
```ts
import { UsersRepository } from '@/repositories/usersRepository'
import { hash } from 'bcryptjs'
import { UserAlreadyExistsError} from './erros/userAlreadyExistsError'
import { User } from '@prisma/client'

interface RegisterUseCaseRequest {
	name: string
	email: string
	passoword: string
}

interface RegisterUseCaseRespone {
	user: User
}

export class RegisterUseCase {
	

	constructor(private usersRepository: any) {
		this.usersRepository
	}

	async execute({name, email, password}: RegisterUseCaseRequest): Promise<RegisterUseCaseResponse> {
		const passwordHashed = await hash(password, 6)
		const userWithSameEmail = await this.usersRepository.findByEmail(email)

		if(userWithSameEmail) {
			throw new UserAlreadyExistsError()
		}
	
		const user = await this.usersRepository.create({
			name,
			email,
			password
		})

		return { user }
	}
}
```
- Voltando ao nosso arquivo de testes agora, podemos buscar o `user`gerado.
```ts
import { expect, describe, it } from 'vitest'
import { compare } from 'bcryptjs'

describe('Register Use Case', () => {
	it('should hash user password upon registration', () => {
		const prismaUsersRepository = new PrismaUsersRepository()
		const registerUseCase = new RegisterUseCase(prismaUsersRepository)
	})

		const { user} = await registerUseCase.execute({
			name: 'John Doe',
			email: 'johndoe@email.com',
			password: '123456'
		})

		const isPasswordCorrectlyHashed = await compare('123456', user.password)

		expect(isPasswordCorrectlyHashed).toBe(true)
})
```
- Mas o teste acima, não é um teste unitário, pois ele faz o uso de dependências, como *banco de dados*, e isso o torna um teste de integração.
- Para tornar esse teste unitário, podemos fazer as seguintes alterações:
```ts
import { expect, describe, it } from 'vitest'
import { compare } from 'bcryptjs'

describe('Register Use Case', () => {
	it('should hash user password upon registration', () => {
		const registerUseCase = new RegisterUseCase({
			async findByEmail(email) {
				return null
			}

			async create(data) {
				return {
					id: 'user-1',
					name: data.name,
					email: data.email,
					password: data.email,
					created_at: new Date(),
				}
			}
		})
	})

		const { user} = await registerUseCase.execute({
			name: 'John Doe',
			email: 'johndoe@email.com',
			password: '123456'
		})

		const isPasswordCorrectlyHashed = await compare('123456', user.password)

		expect(isPasswordCorrectlyHashed).toBe(true)
})
```
- Desta maneira estamos testando apenas a funcionalidade de fazer o `hash`da senha do nosso usuário.
