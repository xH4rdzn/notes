___
- Agora vamos criar um método para fazer um resumo da conta, em outras palavras o valor total do pedido, que pode ser utilizado para realizar o pagamento.
- No `ordersController`, vamos adicionar:
```ts
async show(request: Request, response: Response, next: NextFunction) {
	try {
		const { table_session_id } = request.params


		const order= await knex("orders")
			.select(
				knex.raw("COALESCE(SUM(orders.price * orders.quantity), 0) as total"),
				knex.raw("COALESCE(SUM(orders.quantity), 0) as total"),
			)
			.where({ table_session_id})
			.first()

		return response.json()
	} catch(error) {
		next(error)
	}
}
```
- E agora adicionamos essa rota em nosso `ordersRoutes`, da seguinte maneira:
```ts
ordersRoutes.get("/table-session/:table_session_id/total", ordersController.show)
```