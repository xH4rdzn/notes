___
- Todos os testes, devem ser excluídos de qualquer contexto.
- Jamais podemos escrever um teste que depende de outro teste. Se isso acontece, eles deveriam ser apenas um teste.
```ts
it('should be able to list all transactions', async() => {
	const createTransactionResponse = await request(app.server)
		.post('/transactions')
		.send({
			title: 'New Transaction',
			amount: 5000,
			type: 'credit',
		})
		const cookies = createTransactionResponse.get('Set-Cookie')
		const listTransactionResponse = await request(app.server)
			.get('/transactions')
			.set('Cookie', cookies)
			.expect(200)
		expect(listTransactionResponse.body.transactions).toEqual([
			expect.objectContaining({
				title: 'New Transaction',
				amount: 5000,
			})
		])
})
```