___
- [[Recuperando o Usuário|Agora que fizemos a autenticação]] do usuário, precisamos devolver o token para ele;
- Para isso vamos instalar a biblioteca `jsonwebtoken`, com o comando abaixo:
```zsh
npm i jsonwebtoken
```
- E também suas tipagens:
```zsh
npm i --save-dev @types/jsonwebtoken
```
- Agora dentro da pasta `src`, criamos uma pasta com o nome de `configs`;
- Dentro dessa pasta criamos o arquivo `auth.ts`, e dentro desse arquivo, vamos colocar as configurações do token, como no exemplo abaixo:
```ts
export const authConfig = {
	jwt: {
		secret: process.env.JWT_SECRET,
		expiresIn: "1d"
	} 
}
```
- Como estamos utilizando as variáveis de ambiente, voltamos ao arquivo `.env`e colocamos o `JWT_SECRET` lá
```env
JWT_SECRET=igor
```
*Para criar o `secret`, podemos usar um `HASH GENERATOR`, para ficar ainda mais complicado de descobrir o segredo, como estamos estudando podemos usar um texto mais simples;
- Agora voltamos ao nosso `sessionController`, e importamos essas configurações:
```ts
import { authConfig } from "@/configs/auth"
import { sign } from "jsonwebtoken"
```
- Após as importações adicionamos no nosso controller:
```ts
import { Request, Response } from "express"
import { AppError } from "@/utils/AppError"
import { prisma } from "@/database/prisma"
import { compare } from "bcrypt"
import { authConfig } from "@/configs/auth"
import { sign } from "jsonwebtoken"
import { z } from "zod"

class SessionsController {
	async create(request: Request, response: Response) {

		const bodySchema = z.object({
			email: z.string().email(),
			password: z.string().min(6),
		})

		const { email, password } = bodySchema.parse(request.body)

		const user = await prisma.user.findFirst({
			where: { email },
		})

		if(!user){
			throw new AppError("Invalid email or password", 401)
		}

		const passwordMatched = await compare(password, user.password)

		if(!passwordMatched){
			throw new AppError("Invalid email or password", 401)
		}

		const { secret, expiresIn } = authConfig.jwt

			const token = sign({role: user.role ?? "customer"}, secret, {
			subject: user.id,
			expiresIn,
		})

		return response.json({ token })
	}
}

export { SessionsController }
```