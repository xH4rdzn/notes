___
- Dentro da pasta `Controllers`, vamos criar um novo arquivo, que vai ser o `controller`, responsável por autenticar o nosso usuário;
- Para isso vamos criar o arquivo `sessionsController.ts`
- E nesse arquivo seguimos o exemplo:
```ts
import { Request, Response } from "express"

class SessionsController {
	create(request: Request, response: Response) {
		return response.json({message: "ok"})
	}
}

export { SessionsController }
```
- Agora podemos criar uma rota para utilizar esse `controller`, para fazer isso vamos na pasta `routes`e criamos o arquivo `sessionsRoutes.ts`, e dentro desse arquivo fazemos o seguinte:
```ts
import { Router } from "express"
import { SessionsController } from "@/controllers/sessionsController"

const sessionsRoutes = Router()
const sessionsController = new SessionsController()

sessionsRoutes.post("/", sessionsController.create)


export { sessionsRoutes }
```
- Ainda dentro da pasta `routes`, vamos no arquivo index e adicionamos o `sessionsRoutes`:
```ts
import { sessionsRoutes } from "./sessionsRoutes"

routes.use("/sessions", sessionsRoutes)
```
*Desta maneira essa rota já deve ficar disponível*


