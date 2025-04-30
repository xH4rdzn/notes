___
- A função que criamos para poder fazer o [[Criação de um usuário|registro de um usuário]], vamos separar ela em um `controller`.
- Para isso dentro da pasta `src`, vamos criar uma pasta com o nome de `http` dentro dessa pasta vamos criar a pasta `controllers`e dentro dela vamos criar o arquivo `register.ts` e dentro desse arquivo vamos criar a função que é responsável por fazer o registro do usuário:
```ts
import { FastifyRequest, FastifyReply } from 'fastify'
import { prisma } from '@/lib/prisma'
import { z } from 'zod'

export async function register(request: FastifyRequest, reply: FastifyReply) {
	const bodySchema = z.object({
		name: z.string(),
		email: z.string().email(),
		password: z.string().min(6),
	})

	const {name, email, password } = bodySchema.parse(request.body)

	await prisma.user.create({
		data: {
			name,
			email,
			password,
		}
	})

	return reply.status(201).send()
}
```
- Agora vamos separar as rotas, então dentro da pasta `http`, vamos criar o arquivo `routes.ts` e dentro desse arquivo vamos fazer o seguinte:
```ts
import { FastifyInstance } from 'fastify'
import { register } from './controllers/register'

export async function appRoutes(app: FastifyInstance) {

	app.post('/users', register)

}
```
- Voltamos ao arquivo `app.ts` e adicionamos a linha:
```ts
import { appRoutes } from './http/routes'

app.register(appRoutes)
```