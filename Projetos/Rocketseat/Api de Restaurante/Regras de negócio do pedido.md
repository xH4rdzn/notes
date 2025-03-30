___
- Agora vamos criar algumas validações, que são as regras de negócio da nossa aplicação;
- Então nosso *controller* de pedidos, vamos adicionar:
```ts
import { Request, Response, NextFunction } from 'express'
import { z } from 'zod'
import { knex } from "@/database/knex"
import { AppError } from "@/utils/AppError"

export class OrdersController {
	async create(request: Request, response: Response, next: NextFunction) {
		try {
			const bodySchema = z.object({
				table_session_id: z.number(),
				product_id: z.number(),
				quantity: z.number(),
			})

			const { table_session_id, product_id, quantity } = bodySchema.parse(request.body)


			const session = await knex<TablesSessionsRepository>("tables_sessions").where({ id: table_session_id}).first()

			if(!session) {
				throw new AppError("session table not found")
			}

			if(session.closed_at) {
				throw new AppError("this table is closed")
			}

			const product = await knex<ProductRepository>("products").where({ id: product_id }).first()


			if(!product) {
				throw new AppError("Product not found")
			}

			return response.status(201).json()
	
		} catch(error) {
			next(error)
		}
	}
}
```