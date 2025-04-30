___
- Para poder realizar as requisições dos testes, vamos usar uma ferramenta chamada *supertest*, e para instalar vamos usar o comando:
```zsh
npm i supertest -D
```
- E também suas tipagens:
```zsh
npm i @types/supertest -D
```
- Agora vamos separar a nossa aplicação em dois arquivos o `app.ts`e o `server.ts`
```ts
// app.ts
import fastify from 'fastify'
import cookie from '@fastify/cookie'

import { transactionsRoutes } from './routes/transactions'

export const app = fastify()

app.register(cookie)
app.register(transactionsRoutes, {
	prefix: 'transactions',
})

// server.ts

import { app } from './app'
import { env } from './env'

app.listen({
	port: env.PORT
}).then(() => {
	console.log('HTTP Server Running!')
})
```
- Agora voltamos ao arquivo de teste e fazemos da seguinte maneira:
```ts
// example.test.ts
import { expect, test, beforeAll } from 'vitest'
import request from 'supertest'
import { app } from './src/app'

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
```
- Usamos a função *beforeAll*, para executar uma função antes de todos os testes executem, mas essa função vai ser executada apenas uma vez antes de todos os testes.
- Se quisermos executar esse código mais vezes antes de cada teste usamos a função *beforeEach*.
- E também temos o *afterAll* e *AfterEach*, que são usamos para executar depois.