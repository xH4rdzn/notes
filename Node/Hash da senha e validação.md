___
- Para criarmos o *hash* da senha vamos usar o `bcryptjs`, e vamos instalar ele usando:
```zsh
npm i bcryptjs
```
- E também precisamos instalar suas tipagens, com o comando:
```zsh
npm i @types/bcryptjs -D
```
- Agora voltamos ao nosso `register`[[Controller de registro|controller]] e adicionamos
```ts
import { FastifyRequest, FastifyReply } from 'fastify'
import { hash } from 'bcryptjs'
import { prisma } from '@/lib/prisma'
import { z } from 'zod'

export async function register(request: FastifyRequest, reply: FastifyReply) {
	const bodySchema = z.object({
		name: z.string(),
		email: z.string().email(),
		password: z.string().min(6),
	})

	const {name, email, password } = bodySchema.parse(request.body)

	const passwordHashed = await hash(password, 6)

	const userWithSameEmail = await prisma.user.findUnique({
		where: {
			email,
		},
	})

	if(userWithSameEmail) {
		return reply.status(409).send()
	}

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
