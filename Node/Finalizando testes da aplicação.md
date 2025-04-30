___
- Voltamos ao nosso arquivo de testes e adicionamos os testes:
```Ts
// Verificando uma transação especifica
it('should be able to get a specific transaction', async() => {
	const createTransactionResponse = await request(app.server)
		.post('/transactions')
		.send({
			title: 'New Transaction',
			amount: 5000,
			type: 'credit',
		})
	const cookies = createTransactionResponse,get('Set-Cookie')
	
	const listTransactionResponse = await request(app.server)
			.get('/transactions')
			.set('Cookie', cookies)
			.expect(200)

	const transactionId = listTransactionResponse.body.transactions[0].id

	const getTransactionResponse = await request(app.server)
		.get(`/transactions/${transactionId}`)
		.set('Cookie', cookies)
		.expect(200)

	expect(getTransactionResponse.body.transaction).toEqual(
		expect.objectContaining({
			title: 'New Transaction',
			amount: 5000,
		}),
	)
		
})

it('should be able to get the summary', async () => {
	const createTransactionResponse = await request(app.server)
		.post('/transactions')
		.send({
			title: 'Credit Transaction',
			amount: 5000,
			type = 'credit'
		})

	const cookies = createTransactionResponse.get('Set-Cookie')

	await request(app.server)
		.post('/transactions')
		.set('Cookie', cookies)
		.send({
			title: 'Debit Transaction',
			amount: 2000,
			type: 'debit',
		})

	const summaryResponse = await request(app.server)
		.get('/transactions/summary')
		.set('Cookie', cookies)
		.expect(200)

	expect(summaryResponse.body.summary).toEqual({
		amount: 3000,
	})
})
```
- Desta maneira finalizamos todos os testes *E2E* da nossa aplicação.