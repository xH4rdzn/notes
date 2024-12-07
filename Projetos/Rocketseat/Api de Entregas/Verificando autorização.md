___
- Agora que já temos a parte de **autenticação**, vamos implementar a parte de **autorização**
- Na pasta de `middlewares`, vamos criar o arquivo `verifyUserAuthorization.ts`;
- E fazemos como no exemplo a seguir:
```ts
import { Request, Response, NextFunction } from "express"
import { AppError } from "@/utils/AppError"

export function verifyUserAuthorization(role: string[]){
	return (request: Request, response: Response, next: NextFunction) => {

		if(!request.user){
			throw new AppError("Unauthorized", 401)
		}

		if(!role.includes(request.user.role)){
			throw new AppError("Unauthorized", 401)
		}

		return next()
	
	}
}
```
- Agora podemos utilizar esse `middleware`, no nossas rotas de `deliveriesRoutes`, e o passamos depois do `ensureAuthenticated`, da seguinte maneira:
```ts
deliveriesRoutes.use(ensureAuthenticated, verifyUserAuthorization(["sale"]))
```
- Desta maneira apenas o usuário que é do tipo `sale`, vai ter acesso a essas rotas;