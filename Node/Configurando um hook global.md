___
- Pode existir *middlewares* ou *handlers* que queremos que executem em todas as rotas da nossa aplicação. Isso é de maneira global.
- Devemos prestar atenção que cada parte separada que criamos no `fastify`é como se fosse um **plugin** e isso da um contexto isolado para cada **plugin**;
- Em outras palavras mesmo que criamos um hook global, se ele estiver dentro de um **plugin** ele só irá existir de maneira global para aquele plugin.
- Para criar um *handler* global, fazemos como no exemplo abaixo:
```ts
export async function transactionsRoutes(app: FastifyInstance) {
	app.addHook('preHandler', async(request, reply) => {
		
	})
}
```
- Se quisermos que esse *handler* seja executado em todos os contextos da nossa aplicação devemos criar ele no arquivo `server.ts`;