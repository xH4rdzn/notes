___
- O código usado anteriormente para ler os dados do corpo da requisição, podemos deixar ele separado em outro arquivo.
- Chamamos esse conceito de ***middlewares***, eles são interceptadores, eles são normalmente identificados pois eles sempre recebem o `req` e o `res`. Eles são responsáveis por transformar a nossa requisição ou resposta.
- Para isso dentro da pasta *src*, vamos criar a pasta ***middlewares*** e dentro dessa pasta vamos criar o arquivo `json.js`
```js
export async function json(req, res) {
	const buffers = []
	
	for await (const chunk of req) {
		buffers.push(chunk)
	}
	
	try {
		req.body = JSON.parse(Buffer.concat(buffers).toString())
	} catch {
		req.body = null
	}
	
	res.setHeader('Content-Type', 'application/json')
}
```
- Agora dentro do nosso `server.js`, importamos essa função e passamos o `req` e o `res`do nosso servidor Node.
```js
await json(req, res)
```
