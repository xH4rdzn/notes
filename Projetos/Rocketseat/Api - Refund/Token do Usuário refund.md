___
- Agora dentro da pasta `src`, vamos criar uma pasta com o nome de `configs`, dentro dessa pasta vamos criar o arquivo `auth.ts`;
```ts
export const authConfig = {
	jwt: {
		secret: "igor",
		expiresIn: "1d",
	}
}
```
- Agora vamos instalar o `jsonwebtoken`, com o comando:
```zsh
npm i jsonwebtoken
```
- E suas tipagens:
```zsh
npm i @types/jsonwebtoken -D
```
- Agora voltamos ao `SessionsController`e adicionamos:
```ts
import { Request, Response } from 'express'
import { AppError } from "@/utils/AppError"
import { authConfig } from "@/configs/auth"
import { prisma } from "@/database/prisma"
import { sign } from 'jsonwebtoken'
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

		const { secret, expiresIn } =  authConfig.jwt
		const token = sign({role: user.role}, secret, {
			subject: user.id,
			expiresIn,
		})

		const {password: _, ...userWithoutPassword } = user

		response.json({ token, user: userWithoutPassword })
	}
}

export { SessionsController }
```