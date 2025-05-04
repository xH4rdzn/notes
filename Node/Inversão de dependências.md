___
- Uma das motivações de usar o [[Repository Pattern]], é conseguir migrar de ferramenta, banco de dados, do que estamos usando na nossa aplicação.
- *SOLID* -> É dividido em 5 partes onde:
	- *D* -> Dependecy Inversion Principle (Inversão de depêndencia.)
- Como diz o próprio nome desse principio, vamos inverter a ordem de como a dependência chega no nosso caso de uso.
- Em outras palavras vamos receber essas dependências como parâmetro.
- Então o nosso caso de uso que era uma função vamos transformar ele em classe.
- **Cada caso de uso, vai ter apenas um método.**
```ts
export class RegisterUseCase {
	

	constructor(private usersRepository: any) {
		this.usersRepository
	}

	async execute({name, email, password}:) {
		await this.usersRepository.create({
			name,
			email,
			password
		})
	}
}
```
- Agora para utilizar essas dependências no arquivo que faz o uso desse `useCase`deve enviar as dependências.
- Como no nosso controller que ficaria assim:
```ts
// Register.ts Controller
import { FastifyRequest, FastifyReply } from 'fastify'
import { z } from 'zod'
import { RegisterUseCase } from '@/useCases/register'
import { PrismaUsersRepository } from '@/repositories/prismaUsersRepository'
export async function register(request: FastifyRequest, reply: FastifyReply) {
	const bodySchema = z.object({
		name: z.string(),
		email: z.string().email(),
		password: z.string().min(6),
	})

	const { name, email, password } = bodySchema.parse(request.body)

	 try {
		const prismaUsersRepository = new PrismaUsersRepository()
		const registerUseCase = new RegisterUseCase(prismaUsersRepository)
		 await registerUseCase.execute({
			 name,
			 email,
			 password
		 })
	 } catch(err) {
		 return reply.status(409).send()
	 }
}
```