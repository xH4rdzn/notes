___
- Agora na pasta `controllers`, vamos criar o arquivo `refundsController.ts` e vamos criar:
```ts
import { Request, Response } from 'express'

class RefundsController {
	async create(request: Request, response: Response){
		return response.json({message: "ok"})
	}
}

export { RefundsController}
```
- Agora na pasta `routes`, vamos criar o arquivo `refundsRoutes.ts`, e dentro dele vamos fazer:
```Ts
import { Router } from 'epxress'
import { RefundsController } from "@/controllers/refundsController"

const refundsRoutes = Router()
const refundsController = new RefundsController()

refundsRoutes.post("/", refundsController.create)

export { refundsRoutes }
```
- Agora na pasta `routes`, no arquivo `index.ts`, vamos adicionar o `refundsRoutes`
```Ts
import { refundsRoutes } from './refundsRoutes'

// Rotas Privadas
routes.use("/refunds", refundsRoutes)
```
- E agora configuramos no `Insomnia`, para podermos testar o endpoint;