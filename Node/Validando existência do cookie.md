___
- Agora nas rotas de listagem de transações, precisamos buscar apenas as transações feitas naquela sessão, daquele usuário;
- Então podemos fazer da seguinte maneira:
```ts
app.get('/', async (request, reply) => {
	const sessionId = request.cookies.sessionId

	if(!sessionId) {
		return reply.status(401).send({
			error: 'Unauthorized'
		})
	}

	const transactions = await knex('transactions')
		.where('session_id', sessionId)
		.select()
})
```
- Como parte desse código vai aparecer nas outras rotas, precisamos de uma maneira para reaproveitar ele, para poder validar em todas as rotas;
- Para fazer isso, na pasta `src`, vamos criar a pasta `middlewares`e dentro dessa pasta vamos criar o `checkSessionIdExists.ts`e dentro dele fazemos o seguinte código:
```ts
export async function checkSessionIdExists(request: FastifyRequest, reply: FastifyReply) {
	const sessionId = request.cookies.sessionId

	if(!sessionId) {
		return reply.status(401).send({
			error: 'Unauthorized.'
		})
	}
}
```
- Agora voltamos a rota em que queremos que esse `middleware`seja executado e fazemos da seguinte maneira:
```ts
app.get('/', {
	preHandler: [checkSessionIdExists],
} , async (request, reply) => {
	//
})
```
- Agora basta aplicarmos esse `middleware`nas rotas onde desejamos que seja o mesmo `sessionId`;