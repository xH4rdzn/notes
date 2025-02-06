___
- Agora vamos fazer uma rota de um resumo de todas as transações feitas em sua conta.
- Para isso vamos seguir o exemplo abaixo:
```ts
app.get('/summary', async () => {
	const summary = await knex('transactions').sum('amount', { as: 'amount' })

	return { summary }
})
```
- Usamos o método `sum`, para retornar todos os valores da conta;
- O segundo parâmetro do método `sum`, podemos usar o `as`, e assim dar um nome para essa coluna;