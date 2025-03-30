___
- Agora dentro da pasta `middlewares`, vamos criar um novo arquivo, com o nome de `ensureAuthenticated.ts` e dentro dele vamos fazer o seguinte:
```ts
import { Request, Response, NextFunction } from 'express'
import { verify } from 'jsonwebtoken'
import { authConfig } from '@configs/auth'
import { AppError } from '@/utilsAppError'

interface TokenPayload {
	role: string
	sub: string
}

export function ensureAuthenticated(request: Request, response: Response, next: NextFunction) {
	try {
		const authHeader = request.headers.authorization

		if(!authHeader) {
			throw new AppError("JWT token não encontrado")
		}
		
		const [, token] = authHeader.split(" ")
		
		const { role, sub: user_id } = verify(token, authConfig.jwt.secret) as TokenPayload


		request.user = {
			id: user_id,
			role,
		}

		return next()

	} catch(error) {
		throw new AppError("JWT Token inválido", 401)
	}
}
```
- Agora dentro da pasta `src`, vamos criar uma pasta com o nome de `types`, e dentro dela vamos criar o arquivo `express.d.ts` e nele fazemos o seguinte:
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
- Agora voltamos ao nosso controller;
- Agora vamos em nosso arquivo `index.ts`, que está dentro da pasta `routes` e adicionamos o nosso *middleware* da seguinte maneira:
```ts
import { ensureAuthenticated } from "@/middlewares/ensureAuthenticated"

// Rotas privadas
routes.use(ensureAuthenticated)
routes.use("/refunds", refundsRoutes)
```