___
- Para definir quais papeis de usuário e quais rotas ele tem autorização, vamos utilizar um *middleware*, para fazer isso.
- Dentro da pasta `middleware`, que criamos, vamos criar o arquivo `verifyUserAuthorization.ts`, e dentro desse arquivo vamos criar o seguinte código:
```ts
import { Request, Response, NextFunction } from "express"
import { AppError } from "@/utils/AppError"

function verifyUserAuthorization(role: string[]) {

	return (request: Request, response: Response, next: NextFunction) => {
		if(!request.user || !role.inclues(request.user.role)){
			throw new AppError("Unauthorized", 401)
		}

		return next()
	}
}

export { verifyUserAuthorization }
```
- E agora passamos esse *middleware* para as rotas que queremos que seja acessada apenas por usuários que possuem a permissão, em nosso controller;
```ts
productsRoutes.post(
"/",
ensureAuthenticated,
verifyUserAuthorization(["sale", "admin"])
)
```
*Nota-se que a ordem dos `middlewares` são importantes;*
- No array da função `verifyUserAuthorization` passamos os papeis que podem acessar essa rota;