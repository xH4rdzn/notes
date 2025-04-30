___
- Podemos categorizar os nossos testes, para isso vamos usar o `describe`como no exemplo abaixo:
```ts
import { test, beforeAll, afterAll, describe } from 'vitest'
import request from 'supertest'
import { app } from './src/app'

describe('Transactions Routes', () => {
	beforeAll( async () => {
		await app.ready()
	})

	afterAll(async () => {
		await app.close()
	})

	test('O usuário consegue criar uma nova transação', async () => {
		await request(app.server)
			.post('/transactions')
			.send({
				title: "New Transaction",
				amount: 5000,
				type: 'credit'
			})
			.expect(201)
	})
})
```
- Para criar as nossos testes podemos usar a função `test`ou a função `it`;
