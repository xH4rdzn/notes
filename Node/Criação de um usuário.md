___
- Vamos criar essa rota inicialmente da maneira mais simples possível, para isso vamos no arquivo `app.ts`e nela vamos adicionar:
```ts
import { z } from 'zod'
import { prisma } from './lib/prisma'

app.post('/users', async (request, reply) => {
	const registerBodySchema = z.object({
		name: z.string(),
		email: z.string().email(),
		password: z.string().min(6),
	})

	const { name, email, password } = registerBodySchema.parse(request.body)
})

	await prisma.user.create({
		data: {
			name,
			email,
			password_hash: password,
		}
	})

	return reply.status(201).send()
```
- Dentro da pasta `src`, vamos criar a pasta `lib`e criar o arquivo `prisma.ts`e dentro dele fazemos o seguinte:
```ts
import { PrismaClient } from '@prisma/client'

export const prisma = new PrismaClient({
	log: env.NODE_ENV === 'dev' ? ['query'] : [],
})
```
- Agora vamos começar a estruturar melhor a nossa aplicação.