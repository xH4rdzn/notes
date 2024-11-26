___
- Em algumas aplicações, em certas regras de negócio, precisamos restringir o acesso a todos os usuários, para isso precisamos definir o papel de cada usuário;
- Para isso precisamos voltar onde [[Criando Sessão|criamos]] a nossa sessão e alteramos o código para a seguinte maneira:
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

	const token = sign({ role }, secret, {
		expiresIn,
		subject: String(user.id)
	})

	return response.json({ token })
}
```
- Agora voltamos ao nosso [[Middleware de Autenticação|middleware]] e recuperamos essa informação:
```ts
import { Request, Response, NextFunction } from "express"
import { AppError } from "src/utils/AppError"
import { verify } from "jsonwebtoken"
import { authConfig } from "src/configs/auth"

export function ensureAuthenticated(request: Request, response: Response, next: NextFunction) {
	const authHeader = request.headers.authorization
	
	if(!authHeader) {
		throw new AppError("JWT Token não informado", 401)
	}
	
	const [, token] = authHeader.split(" ")

	const { sub: user_id, role } = verify(token, authConfig.jwt.secret)
	request.user = {
		id: user_id
	}

	return next()
}
```
- Porém o `typescript`não vai entender o `role`, para isso podemos criar uma interface passando as informações que ele vai receber ficando como no exemplo abaixo:
```ts
import { Request, Response, NextFunction } from "express"
import { AppError } from "src/utils/AppError"
import { verify } from "jsonwebtoken"
import { authConfig } from "src/configs/auth"

interface TokenPayload {
	role: string
	sub: string
}

export function ensureAuthenticated(request: Request, response: Response, next: NextFunction) {
	const authHeader = request.headers.authorization
	
	if(!authHeader) {
		throw new AppError("JWT Token não informado", 401)
	}
	
	const [, token] = authHeader.split(" ")

	const { sub: user_id, role } = verify(token, authConfig.jwt.secret) as TokenPayload
	request.user = {
		id: user_id,
		role
	}

	return next()
}
```
- E como definimos uma tipagem para o `Express`, precisamos fazer a alteração para que ele entenda o `role`, alterando para:
```ts
declare namespace Express {
	export interface Request {
		user?: {
			id: string
			role: string
		}
	}
}
```