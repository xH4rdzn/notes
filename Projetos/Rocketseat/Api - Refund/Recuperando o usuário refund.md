___
- Agora vamos recuperar o usuário, para isso vamos continuar no nosso `SessionsController`
```ts
import { Request, Response } from 'express'
import { AppError } from "@/utils/AppError"
import { prisma } from "@/database/prisma"
import { compare } from "bcrypt"
import { z } from 'zod'

class SessionsController {
	async create(request: Request, response: Response) {
		const bodySchema = z.object({
			email: z.string().email({ message: 'E-mail inválido'}),
			password: z.string(),
		})

		const { email, password } = bodySchema.parse(request.body)

		const user = await prisma.user.findFirst({ where: {email }})

		if(!user){
			throw new AppError('E-mail ou senha inválido', 401)
		}

		const passwordMatched = await compare(password, user.password)

		if(!passwordMatched) {
			throw new AppError('E-mail ou senha inválido', 401)
		}

		

		response.json({ message: "ok"})
	}
}

export { SessionsController }
```