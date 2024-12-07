___
- Dentro da pasta `controllers`, vamos criar o arquivo `deliveriesController.ts`;
- Neste arquivo fazemos:
```ts
import { Request, Response } from "express"

export class DeliveriesController {
	create(request: Request, response: Response) {
		return response.json({ message: "ok"})
	}
}
```
- Agora na pasta `routes`, criamos o arquivo `deliveriesRoutes.ts` e fazemos o seguinte:
```ts
import { Router } from "express"
import { DeliveriesController } from "@/controllers/deliveriesController"

const deliveriesRoutes = Router()
const deliveriesController = new DeliveriesController()

deliveriesRoutes.use(ensureAuthenticated)
deliveriesRoutes.post("/", deliveriesController.create)


export { deliveriesRoutes }
```
- Agora dentro da pasta `routes`, no arquivo `index.ts`, importamos o `deliveriesRoutes`, e usamos ele:
```ts
import { deliveriesRoutes } from "./delieriesRoutes"

routes.use("/deliveries", deliveriesRoutes)
```