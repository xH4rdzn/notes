___
- Criamos o arquivo `authenticate.spec.ts` e dentro dele vamos fazer os testes:
```Ts
import { InMemoryUsersRepository } from '@/repositories/inMemory/InMemoryUsersRepository'

import { expect, describe, it} from 'vitest'

describe('Authenticate Use Case', () => {
	it('should be able to authenticate', async () => {
		const usersRepository = new InMemoryRepository()
		const sut = new AuthenticateUseCase(usersRepository)

		const { user } = await sut.execute({
			email: 'johndoe@email.com',
			password: '123456',
		})

		expect(user.id).toEqual(expect.any(String))
	})

	it('should not be able to authenticate with wrong email', async() => {
		const usersRepository = new InMemoryUsersRepository()
		const sut = new AuthenticateUseCase(usersRepository)

		expect(() => sut.execute({
			email: 'johndoe@email.com',
			password: '123456'
		})
		).rejects.toBeInstanceOf(InvalidCredentialsError)
	})


	it('should not be able to authenticate with wrong password', async() => {
		const usersRepository = new InMemoryUsersRepository()
		const sut = new AuthenticateUseCase(usersRepository)

		await usersRepository.create({
			name: 'John Doe',
			email: 'johndoe@email.com',
			password: await hash('123456', 6)
		})

		expect(() => sut.execute({
			email: 'johndoe@email.com',
			password: '123123'
		})
		).rejects.toBeInstanceOf(InvalidCredentialsError)
	})
})
```
- Com a parte dos testes finalizadas, podemos ir para o nosso controller.
- Dentro da pasta `controllers`, podemos fazer o arquivo `authenticate.ts`e dentro dele vamos fazer o seguinte:
```ts
import { FastifyRequest, FastifyReply } from 'fastify'
import { z } from 'zod'
import { PrismaUsersRepository } from '@/repositories/prisma/PrismaUsersRepository'

export async function authenticate(request: FastifyRequest, reply: FastifyReply) {
	const bodySchema = z.object({
		email: z.string().email(),
		password: z.string()
	})

	const { email, password } = bodySchema.parse(request.body)

	try {
		const usersRepository = new PrismaUsersRepository()
		const authenticateUseCase = new AuthenticateUseCase(usersRepository)

	await authenticateUseCase.execute({
		email,
		password
	})

	} catch(err) {
		if(err instanceof InvalidCrentialsError) {
			return reply.status(400).send({message: err.message})
		}

		throw err
	}

	return reply.status(200).send()
}
```
- Agora vamos criar uma rota para usar esse controller, no nosso arquivo `routes.ts`e vamos criar uma rota:
```ts
import { FastifyInstance } from 'fastify'
import { authenticate } from './controllers/authenticate'
import { register } from './controllers/register'

export async function appRoutes(app: FastifyInstance) {
	app.post('/users', register)

	app.post('/sessions', authenticate)
}

```