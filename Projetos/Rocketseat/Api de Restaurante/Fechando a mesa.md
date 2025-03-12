___
- Agora para fechar a mesa:
```ts
async update(request: Request, response: Response, next: NextFunction) {
	try {
		const id = z
		 .string()
		 .transform((value) => Number(value))
		 .refine((value) => !isNaN(value), { message: "id must be a number"})
		 .parse(request.params.id)

		const session = await knex<TablesSessionsRepository>("tables_sessions").where({ id }).first()

		if(!session) {
			throw new AppError("Essa mesa não está em uso")
		}


		if(session.closed_at) {
			throw new AppError("Essa mesa já está fechada")	
		}

		await knex<TablesSessionsRepository>("tables_sessions").update({
			closed_at: knex.fn.now()
		}).where({ id })

		return response.json()
	} catch(error){
		next(error)
	}
}
```