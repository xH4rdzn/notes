___
- Após [[Extraindo o Token|extrairmos o token]], precisamos ainda terminar esse *middleware*, para de fato podermos usar essa rota para o usuário autenticado;
- Precisamos importar o `verify`e o `authConfig`, que criamos [[JSON Web Token|anteriormente]];
```ts
import { verify } from "jsonwebtoken"
import { authConfig } from "src/configs/auth"
```
- Como extraímos o nosso [[Extraindo o Token|token]], usamos o `verify`, para verificar se esse token é valido e também passamos as nossas configurações, como no exemplo abaixo:
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

	verify(token, authConfig.jwt.secret)

	return next()
}
```
- Agora podemos adicionar na requisição a  informação de que o usuário está logado em nossa aplicação, para isso desestruturamos de `verify` o  `sub`, como no exemplo abaixo:
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

	const { sub } = verify(token, authConfig.jwt.secret)

	return next()
}
```
- E passamos a informação para a nossa requisição:
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

	const { sub: user_id } = verify(token, authConfig.jwt.secret)
	request.user = {
		id: user_id
	}

	return next()
}
```
- Mas como no Typescript não conhece o `request.user`, ele vai reclamar então precisamos criar uma nova tipagem;
- Para isso vamos criar uma pasta dentro de `src` com o nome de `types`, e dentro dessa pasta criamos o arquivo: `express.d.ts` e dentro desse arquivo colocamos o seguinte código:
```ts
declare namespace Express {
	export interface Request {
		user?: {
			id: number
		}
	}
}
```
- Agora o `typescript` conhece o `user`, e podemos usar ele em nossas requisições;
