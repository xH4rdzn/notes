___
- Agora vamos salvar o pedido no nosso banco de dados, mas antes vamos criar a tipagem para essa tabela, então dentro da pasta `database`vamos na pasta `types`e dentro da pasta `types`, vamos criar o arquivo `orderRepository.d.ts`e dentro dele vamos fazer o seguinte:
```Ts
type OrderRepository = {
	id: number
	table_session_id: number
	product_id: number
	quantity: number
	price: number
	created_at: number
	updated_at: number
}
```
- Então agora voltamos ao nosso *controller* de pedidos e continuamos:
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


			await knex<OrderRepository>("orders").insert({
				product_id,
				table_session_id,
				quantity,
				price: product.price
			})

			return response.status(201).json()
	
		} catch(error) {
			next(error)
		}
	}
}
```
- Desta maneira já estamos adicionado itens nos pedidos;