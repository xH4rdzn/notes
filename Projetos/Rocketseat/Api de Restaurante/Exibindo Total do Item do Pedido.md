___
- Ainda no método `index`do `ordersController`, vamos continuar:
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
			"orders.quantity",
			knex.raw("(orders.price * orders.quantity) as total"),
			"orders.created_at",
			"orders.updated_at"
			)
		.join("products", "products.id", "orders.product_id")
		.where({ table_session_id })
		.orderBy("orders.created_at", "desc")
		
		return response.json()
	} catch(error) {
		next(error)
	}
}
```