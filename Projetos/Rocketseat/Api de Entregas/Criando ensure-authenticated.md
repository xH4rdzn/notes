___
- Agora na pasta `middlewares`, vamos criar um para autenticação;
- Damos o nome de `ensureAuthenticated.ts`e fazemos como no exemplo abaixo:
```ts
import { Request, Response, NextFunction } from "express"
import { verify } from "jsonwebtoken"
import { authConfig } from "@/configs/auth"
import { AppError } from "@/utils/AppError"

interface TokenPayload {
	role: string
	sub: string
}

export function ensureAuthenticated(
	request: Request,
	response: Response,
	next: NextFunction) {
		try {
			const authHeader = request.headers.authorization

			if(!authHeader) {
				throw new AppError("JWT Token not found", 401)
			}

			const [ , token] = authHeader.split(" ")
	
			const { role, sub: user_id } = verify(token, authConfig.jwt.secret) as TokenPayload

			request.user = {
				id: user_id,
				role,
			}

			return next()
			
		} catch(error) {
			throw new AppError("Invalid JWT token", 401)
		}
}
```
- Agora precisamos adicionar uma tipagem para o usuário, para ele não reclamar quando mandarmos os dados do usuário pela `request`;
- Para isso, na pasta `src`, vamos criar a pasta `types`, e dentro dessa pasta vamos criar o arquivo `express.d.ts` e dentro desse arquivo fazemos da seguinte maneira:
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