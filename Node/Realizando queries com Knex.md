___
- Para realizar uma `query` de inserir dados no banco de dados com o Knex, podemos seguir o exemplo abaixo:
```ts
app.get('/hello', async () => {
	const transaction = await knex('transactions').insert({
		id: crypto.randomUUID(),
		title: 'Transação de Teste',
		amount: 1000,
	}).returning('*')

	return transaction
})
```
- Para realizar uma busca podemos seguir o exemplo abaixo:
```ts
app.get('/hello', async () => {
	const transactions = await knex('transactions').select('*')

	return transactions
})
```
- Podemos também usar o método `where`, para buscar um registro especifico:
```ts
app.get('/hello', async () => {
	const transactions = await knex('transactions')
	.where('amount', 1000)
	.select('*')

	return transactions
})
```