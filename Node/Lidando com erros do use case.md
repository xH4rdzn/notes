___
- Para cada podermos tratar cada tipo de erro, existem várias maneiras de fazer isso.
- Mas nesse caso podemos usar a seguinte:
- Dentro da pasta `useCases`vamos criar uma pasta `errors`e dentro dessa pasta vamos criar cada arquivo para um tipo de erro.
- Nesse exemplo vamos criar o `userAlreadyExistsError.ts` e dentro dele fazemos o seguinte:
```ts
export class UserAlreadyExistsError extends Error {
	constructor() {
		super('E-mail already exists.')
	}
}
```
- Agora no nosso caso de uso alteramos para o seguinte:
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
			throw new UserAlreadyExistsError()
		}
	
		await this.usersRepository.create({
			name,
			email,
			password
		})
	}
}
```
- E agora no nosso `controller` dentro do *catch* fazemos a seguinte verificação:
```ts
try{
	// Código
} catch(err) {
	if(err instanceof UserAlreadyExists) {
		return reply.status(409).send({ message: err.message})

	return reply.status(500).send()
	

	}
}
```