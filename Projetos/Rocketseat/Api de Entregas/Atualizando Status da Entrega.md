___
- Quando um pedido é cadastrado, ele fica com status de `processing`, agora vamos criar uma rota para atualizar esse status;
- Vamos na pasta de `controllers`, e vamos criar um novo arquivo, com o nome de `deliveriesController.ts`
```ts
import { Request, Response } from "express"
import { prisma } from "@/database/prisma"
import { z } from "zod"

class DeliveriesStatusController {
	async update(request: Request, response: Response) {
		const paramsSchema = z.object({
			id: z.string().uuid(),
		})

		const bodySchema = z.obecjt({
			status: z.enum(["processing", "shipped", "delivered"])
		})

		const { id } paramsSchema.parse(request.params)
		const { status } = bodySchema.parse(request.body)

		await prisma.delivery.update({
			data: {
				status,
			},
			where: {
				id,
			}
		})

		return response.json()
	}
}

export { DeliveriesStatusController}
```
- Agora com o nosso controller pronto, podemos partir para a implementação da rota, vamos fazer no arquivo de `deliveriesRoutes`;
- Fazemos a importação do controller que criamos para atualizar o status:
```Ts
import { DeliveriesStatusController } from "@/controllers/DeliveriesStatusController"
```
- E fazemos a sua instância
```ts
const deliveriesStatusController = new DeliveriesStatusController()
```
- Agora criamos uma rota:
```ts
deliveriesRoutes.patch("/:id/status", deliveriesStatusController.update)
```