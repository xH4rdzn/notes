___
- Do jeito que fizemos a [[Abrindo Mesa|abertura da mesa]], se tentarmos abrir a mesma mesa novamente ele vai deixar, o que não pode, para resolver isso vamos adicionar uma verificação em nosso `controller`
```Ts
import { Request, Response, NextFunction } from "express"

export class TablesSessionsController {
	async create(request: Request, response: Response, next: NextFunction) {
		try {
		 const bodySchema = z.object({
			 table_id: z.number(),
		 })

		const { table_id } = bodySchema.parse(request.body)

		const session = await knex<TablesSessionsRepository>("tables_sessions").where({ table_id }).oderBy("opened_at", "desc").first()

		if(session &&  !session.closed_at) {
			throw new AppError("Essa mesa já está sendo usada")
		}

		await knex("tables_sessions").insert({
			table_id,
			opened_at: knex.fn.now()
		})
		
		 return response.status(201).json()
		} catch(error){
			next(error) 
		}
	}
}

```