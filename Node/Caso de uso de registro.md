___
- Agora vamos separar do [[Hash da senha e validação|controller]] aquela parte que vai ser igual independente de como essa funcionalidade vai ser executada.
- Para fazer isso dentro da pasta `src`, vamos criar a pasta `useCases` ou `services`e dentro dela vamos criar o arquivo `register.ts` e dentro dela vamos colocar o código que pegamos do nosso controller
```ts
import { prisma } from '@/lib/prisma'
import { hash } from 'bcryptjs'

interface RegisterUseCaseRequest {
	name: string
	email: string
	password: string
}

export async function registerUseCase({ name, email, password}: RegisterUseCaseRequest) {
	const passwordHashed = await hash(password, 6)

	const userWithSameEmail = await prisma.user.findUnique({
		where: {
			email,
		}
	})

	if(userWithSameEmail) {
		return reply.status(409).send()
	}

	await prisma.user.create({
		data: {
			name,
			email,
			password: passwordHashed,
		},
	})
}
```
- Agora onde queremos fazer o registro de um usuário, podemos chamar o `registerUseCase`, passando os parâmetros necessários.
```ts
// Register.ts Controller
import { FastifyRequest, FastifyReply } from 'fastify'
import { z } from 'zod'
import { registerUseCase } from '@/useCases/register'

export async function register(request: FastifyRequest, reply: FastifyReply) {
	const bodySchema = z.object({
		name: z.string(),
		email: z.string().email(),
		password: z.string().min(6),
	})

	const { name, email, password } = bodySchema.parse(request.body)

	 try {
		 registerUseCase({
			 name,
			 email,
			 password
		 })
	 } catch(err) {
		 return reply.status(409).send()
	 }
}
```
