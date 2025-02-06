___
- Vamos criar uma rota para listar todas as transações, seguindo o exemplo abaixo:
```ts
app.get('/', async () => {
	const transactions = await knex('transactions').select()

	return { transactions }
})
```
- Também já vamos aproveitar e fazer a rota que buscar por uma transação unica, para isso vamos seguir o exemplo abaixo:
```ts
app.get('/:id', async (request) => {
	const getTransactionParamsSchema = z.object({
		id: z.string().uuid(),
	})

	const { id } = getTransactionParamsSchema.parse(request.params)

	const transaction = await knex('transactions').where('id', id).first()

	return { transaction }
})
```