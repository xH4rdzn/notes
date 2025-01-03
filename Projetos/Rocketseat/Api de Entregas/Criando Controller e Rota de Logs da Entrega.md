___
- Na pasta *controllers*, vamos criar o `deliveryLogsController`;
```ts
import { Request, Response } from "express"

export class DeliveryLogsController {
	async create(request: Request, response: Response) {
		return response.json({message: "ok"})
	}
}
```
*Assim o controller já está criado*
- Agora vamos criar as rotas, que acessam esse controller;
- Dentro da pasta `routes`, criamos o arquivo `deliveryLogsRoutes.ts`
```Ts
import { Router } from "express"

import { DeliveryLogsController } from "@/controllers/deliveryLogsController"
import { ensureAuthenticated } from "@/middlewares/ensureAuthenticated"
import { verifyUserAuthorization} from "@/middlewares/verifyUserAuthorization"

const deliveryLogsRoutes = Router()
const deliveryLogsController = new deliveryLogsController()

deliveryLogsRoutes.post(
	"/",
	ensureAuthenticated,
	verifyUserAuthorization(["sale"]),
	deliveryLogsController.create
	
)

export { deliveryLogsRoutes }
```
*Da maneira que o método `post`está significa que apenas usuários do tipo `sale`, tem acesso*;
- Agora vamos no arquivo `index`e cadastramos essas rotas.
```ts
routes.use("/logs", deliveryLogsRoutes)
```
