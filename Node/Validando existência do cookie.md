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
- Caso precisamos verificar se é o mesmo usuário que está fazendo a requisição, podemos fazer a verificação da seguinte maneira:
```ts
import type { FastifyReply, FastifyRequest } from 'fastify'

import { knex } from '../database'

  

export async function checkingSessionIdExists(

request: FastifyRequest,

reply: FastifyReply,

) {

const sessionId = request.cookies.sessionId

  

if (!sessionId) {

return reply.status(401).send({

error: 'Não autorizado',

})

}

  

const user = await knex('users').where({ session_id: sessionId }).first()

  

if (!user) {

return reply.status(401).send({

error: 'Não autorizado',

})

}

  

request.user = user

}
```
- E passamos o usuário para o `request`, para podermos recuperar em qualquer outra rota.
- Mas também precisamos criar uma tipagem para o `Fastify`, para isso vamos na pasta `types`e criamos o arquivo `fastify.d.ts` e dentro dele adicionamos o seguinte código:
```ts
import 'fastify'

  

declare module 'fastify' {

export interface FastifyRequest {

user?: {

id: string

session_id: string

name: string

email: string

created_at: string

}

}

}
```
- Nota-se que passamos as informações que são do cadastro do usuário;