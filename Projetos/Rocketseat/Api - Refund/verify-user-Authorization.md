___
- Agora vamos verificar se o usuário tem permissão para acessar  ou não uma rota;
- Para isso vamos criar um novo *middleware*, com o nome de `verifyUserAuthorization.ts` e dentro dele vamos fazer:
```Ts
import { Request, Response, NextFunction } from 'express'
import { AppError } from '@/utils/AppError'

export function verifyUserAuthorization(role: string[]) {
	return (request: Request, response: Response, next: NextFunction) => {
		if(!request.user || !role.includes(request.user.role)){
			throw new AppError('Não autorizado', 401)
		}

		return next()
	}
}
```
- Agora vamos no arquivo de rotas `refundRoutes`e adicionamos esse *middleware* onde queremos que apenas um certo perfil tenha acesso a rota:
```Ts
import {verifyUserAuthorization } from "@/middlewares/verifyUserAuthorization"

refundsRoutes.post(
	"/",
	verifyUserAuthorization(["employee"]),
	refundsController.create
)


```