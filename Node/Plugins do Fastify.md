___
- Dentro do *Fastify*, temos os plugins, que nos permitem que separamos a nossa aplicação em varias partes;
- Para podermos separarmos as rotas por exemplo;
- Para fazer isso vamos criar uma pasta com o nome `routes`dentro da pasta `src`;
- E dentro da pasta `routes`, vamos criar um arquivo para as rotas, como por exemplo o arquivo `transactions.ts`, que vai ser responsável por todas as rotas que tenham haver com as transações;
- E esse arquivo vai ficar da seguinte maneira:
```ts
export async function transactionsRoutes(app) {

}
```
- E dentro do nosso arquivo `server.ts`, para podermos usarmos esses plugins, fazemos da seguinte maneira:
```ts
app.register(transactionsRoutes)
```
- **Um ponto importante é que todos os plugins do Fastify precisam ser uma função assíncrona;
- Precisamos tipar o parâmetro que essa função recebe, para isso passamos o `FastifyInstance`, como no exemplo a seguir:
```ts
import { FastifyInstance } from 'fastify'

export async function transactionsRoutes(app: FastifyInstance) {
	app.get('/hello', async () => {
		// código da rota
	})
}
```