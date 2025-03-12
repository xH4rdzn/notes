___
- Agora vamos abrir uma sessão para a mesa, vamos seguir o exemplo:
```ts
import { Request, Response, NextFunction } from "express"

export class TablesSessionsController {
	async create(request: Request, response: Response, next: NextFunction) {
		try {
		 const bodySchema = z.object({
			 table_id: z.number(),
		 })

		const { table_id } = bodySchema.parse(request.body)

		await knex("tables_sessions").insert({
			table_id,
			
		})
		
		 return response.status(201).json()
		} catch(error){
			next(error) 
		}
	}
}
```
- Devemos criar uma tipagem para essa tabela também, então na pasta `types`, criamos o `tablesSessionsRepository.d.ts`
```ts
type TablesSessionsRepository = {
	id: number
	table_id: number
	opened_at: number
	closed_at: number
}
```
- Agora voltamos ao `controller` e passamos essas tipagens:
```ts
import { Request, Response, NextFunction } from "express"

export class TablesSessionsController {
	async create(request: Request, response: Response, next: NextFunction) {
		try {
		 const bodySchema = z.object({
			 table_id: z.number(),
		 })

		const { table_id } = bodySchema.parse(request.body)

		await knex<TablesSessionsRepository>("tables_sessions").insert({
			table_id,
			opened_at: knex.fn.now(),
		})
		
		 return response.status(201).json()
		} catch(error){
			next(error) 
		}
	}
}
```