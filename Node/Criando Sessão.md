___
- Para criar uma sessão devemos ter um controller para criar as sessões;
- Recuperamos os dados do usuário do `request.body`, e fazemos uma verificação, se a senha e o usuário/e-mail são iguais ao que temos no banco de dados, após a verificação podemos criar o nosso token;
```ts
import { Request, Response } from "express"
import { AppError } from "@/utils/AppError"
import { sign } from "jsonwebtoken"
import { authConfig } from "@/configs/auth"
async create(request: Request, response: Response) {

	const { username, password } = request.body

	if(username !== user || password !== userPassword) {
		throw new AppError("Username e/ou senha incorreta", 401)
	}

	const { secret } = authConfig.jwt

	const token = sign({}, secret, {
		expiresIn,
		subject: String(user.id)
	})

	return response.json({ token })
}
```
- Assim podemos devolver o token do usuário, e toda vez que ele logar em nossa aplicação vai ser gerado um token;