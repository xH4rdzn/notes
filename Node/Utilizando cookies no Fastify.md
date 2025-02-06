___
- Cookies -> Formas de manter contexto entre requisições, são muito utilizados principalmente em redes sóciais;
- Para usar essa estrategia de cookies, vamos ter que instalar o plugin do `Fastify`, para isso usamos o comando:
```zsh
npm i @fastify/cookie
```
- Após instalar o pacote acima, voltamos ao arquivo `app.ts` e importamos o pacote da seguinte maneira:
```ts
import cookie from '@fastify/cookie'
```
- Depois da importação precisamos registrar ele em nossa aplicação fazendo da seguinte maneira:
```ts
import fastify from 'fastify'
import cookie from '@fastify/cookie'
// resto das importações

export const app = fastify()


app.register(cookie)
// registro de rotas
```
- Agora vamos onde tudo se inicia, nesse caso quando o usuário cria uma transação, então vamos ao arquivo `transactionsRoutes.ts` e na rota de criação de uma transação adicionamos o seguinte código:
```ts

let sessionId = request.cookies.sessionId

// código de inserir no banco de dados
await knex('transactions').insert({
	title,
	amount: type === 'credit' ? amount : amount * -1,
	// caso exista o sessionId passamos ele nesse momento
	session_id: sessionId
})
```
- Porém se não existir esses cookies, precisamos registra-los, para isso fazemos a verificação da seguinte maneira:
```ts

let sessionId = request.cookies.sessionId

if(!sessionId) {
	sessionId = randomUUID()

	reply.cookie('sessionId', sessionId)
}

// código de inserir no banco de dados
await knex('transactions').insert({
	title,
	amount: type === 'credit' ? amount : amount * -1,
	// caso exista o sessionId passamos ele nesse momento
	session_id: sessionId
})
```
- O `reply`, serve para podermos armazenarmos esses cookies;
- Esses cookies, podem receber configurações, que são passadas da seguinte maneira:
```ts
if(!sessionId) {
	sessionId = randomUUID()

	reply.cookie('sessionId', sessionId, {
		path: '/',
		maxAge: 60 * 60 * 24 * 7,
	})
}
```
- O `path`, significa quais rotas esse cookie vai estar disponíveis, se colocarmos a `/`, qualquer rota da nossa aplicação podem acessar esses cookies;
- O `maxAge`, nos passamos em **milesegundos** o tanto de tempo que esse cookie deve durar no navegador do usuário;
- Os cookies, após de criados são enviados em todas as nossas requisições de maneira automática;