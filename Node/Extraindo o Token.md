___
- Quando o usuário loga na aplicação, através da [[Criando Sessão|criação da sessão]], vai ser devolvido um token, agora precisamos enviar esse token na requisição, para podermos recuperar esse token nas rotas, para esse usuário se identificar;
- Para inserir esse token na nossa requisição vamos utilizar um *middleware*, e para recuperarmos esse token pelo *middleware*, vamos fazer da seguinte maneira:
1. Na raiz do nosso projeto vamos criar uma pasta `middlewares`
2. Dentro dessa pasta vamos criar o arquivo `ensureAuthenticated.ts`
3. Dentro desse arquivos vamos recuperar o token da seguinte maneira:
```ts
import { Request, Response, NextFunction } from "express"

function ensureAuthenticated(request: Request, response: Response, next: NextFunction) {
	const authHeader = request.headers.authorization
	
	if(!authHeader) {
		throw new AppError("JWT Token não informado", 401)
	}
	
	const [, token] = authHeader.split(" ")

	return next()
}

```
4. Agora inserimos esse *middleware*, nas rotas que queremos que o usuário esteja **logado**, para ter acesso