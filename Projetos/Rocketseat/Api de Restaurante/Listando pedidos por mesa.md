___
- Agora vamos dar continuidade em nosso método `index`
```ts
async index(request: Request, response: Response, next: NextFucntion) {
	try {
		const { table_session_id } = request.params

		const order knex("orders")
		.select(
			"orders.id",
			"orders.table_session_id",
			"orders.product_id",
			"products.name",
			"orders.price",
			"orders.quantity"
			)
		.join("products", "products.id", "orders.product_id")
		.where({ table_session_id })
		
		return response.json()
	} catch(error) {
		next(error)
	}
}
```