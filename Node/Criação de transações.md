___
- Como vamos separar nossas rotas por arquivos e cada rota vai ter um endereço para ser acessada, podemos na hora que registramos o plugin do *Fastify*, passar um `prefix`;
```ts
app.register(transactionsRoutes, {
	prefix: 'transactions',
})
```
- Agora em nossas rotas quando formos definir um endereço para acessar um recurso podemos apenas usar o `/`, como no exemplo abaixo:
```ts
export async function transactionsRoutes(app: FastifyInstance) {
	app.post('/', async () => {
		// código aqui
	})
}
``` 
- Agora para criar uma transação, podemos fazer da seguinte maneira:
```ts
export async function transactionsRoutes(app: FastifyInstance) {
	app.post('/', async (request, reply) => {
		const createTransactionBodySchema = z.object({
			title: z.string(),
			amount: z.number(),
			type: z.enum(['credit', 'debit']),
		})

		const { title, amount, type} = createTransactionBodySchema.parse(request.body)

		await knex('transactions').insert({
			id: crypto.randomUUID(),
			title,
			amount: type === 'credit' ? amount : amount * -1,
		})

		return reply.status(201).send()
	})
}
```
- Podemos testar essa rota usando o `Insomnia`;