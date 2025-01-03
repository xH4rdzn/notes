___
- Agora vamos focar no `deliveriesController`;
- Como vamos trabalhar com o banco de dados precisamos o método do controller se torna `async`, pois precisamos aguardar o banco de dados;
- E no método de `create`, podemos fazer da seguinte maneira:
```ts
import { Request, Response } from "express"
import { prisma } from "@/database/prisma"
import { z } from "zod"

class DeliveriesController {
	async create(request: Request, response: Response) {
		const bodySchema = z.object({
			user_id: z.string().uuid(),
			description: z.string(),
		})

		const { user_id, description } = bodySchema.parse(request.body)

		await prisma.delivery.create({
			userId: user_id,
			description
		})

		return response.status(201).json()
	}
}
```
**Lembrando que o `user_id`é o ID do usuário para qual a entrega será realizada. **
