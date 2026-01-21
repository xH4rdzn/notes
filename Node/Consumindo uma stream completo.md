___
- Em alguns, casos, queremos receber todos os dados de uma stream, antes de podermos processar esses dados.
- Para isso no *Node*, podemos fazer da seguinte maneira:
```js
import http from 'node:http'

const server = http.createServer(async (req, res) => {
	const buffers = []
	
	for await (const chunck of req) {
		buffers.push(chunk)
	}
	
	const fullStreamContent = Buffer.concat(buffers).toString()

	console.log(fullStreamContent)

	return res.end(fullStreanContent)
})

server.listen(3334)
```
- Voltando para o nosso arquivo de *stream*, podemos adicionar no *FETCH* da seguinte maneira:
```js
fetch('http://localhost:3334', {
	method: 'POST',
	body: new OneToHundredStream(),
	duplex: 'half'
}).then(response => {
	return response.text()
}).then(data => {
	console.log(data)
})
```