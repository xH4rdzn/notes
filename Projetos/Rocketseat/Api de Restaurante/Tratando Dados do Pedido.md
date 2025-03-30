___
- Agora vamos criar o *controller*, que vai cuidar da parte dos pedidos, para isso vamos criar um novo arquivo na pasta **controllers**, com o nome de `ordersController.ts` e dentro dele vamos fazer o seguinte:
```ts
import { Request, Response, NextFunction } from 'express'
import { z } from 'zod'

export class OrdersController {
	async create(request: Request, response: Response, next: NextFunction) {
		try {
			const bodySchema = z.object({
				table_session_id: z.number(),
				product_id: z.number(),
				quantity: z.number(),
			})

			const { table_session_id, product_id, quantity } = bodySchema.parse(request.body)

			return response.status(201).json()
	
		} catch(error) {
			next(error)
		}
	}
}
```
- Agora precisamos disponibilizar isso em uma rota, então dentro da pasta `routes`, vamos criar o arquivo `ordersRoutes.ts`e dentro dele vamos fazer o seguinte:
```ts
import { Router } from "express"
import { OrdersController } from "@/controllers/ordersController"

const ordersRoutes = Router()
const ordersController = new OrdersController()

orderRoutes.post("/", ordersController.create)

export { ordersRoutes}
```
- Agora vamos ao arquivo `index.ts`que está dentro da pasta `routes`, e adicionamos:
```ts
import { ordersRoutes } from './ordersRoutes'

routes.use("/orders", orderRoutes)
```