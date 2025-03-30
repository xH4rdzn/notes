___
- Agora voltamos a pasta `controllers`, vamos criar um novo arquivo, que vamos chamar de `sessionsController.ts`e dentro dele fazemos o seguinte:
```ts
import { Request, Response } from 'express'


class SessionsController {
	async create(request: Request, response: Response) {
		response.json({ message: "ok"})
	}
}

export { SessionsController }
```
- Agora em nossa pasta `routes`,criamos o arquivo `sessionsRoutes.ts`e dentro dele fazemos o seguinte:
```ts
import { Router } from 'express'
import { SessionsController } from '@/controllers/sessionsController'

const sessionsRoutes = Router()
const sessionsController = new SessionsController()

sessionsRoutes.post("/", sessionsController.create)

export { sessionsRoutes }
```
- Agora no arquivo `index.ts`, que está na pasta `routes`, adicionamos ele logo após a rotas de usuários:
```ts
routes.use("/sessions", sessionsRoutes)
```