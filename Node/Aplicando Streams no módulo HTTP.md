___
- Conseguimos aplicar as *streams* em servidores HTTP, do *NODE*.
- Para isso precisamos, com node puro, podemos criar o servidor da seguinte maneira:
```js
import http from 'node:http'

const server = http.createServer((req, res) => {
	
})

server.listen(3334)
```
- Agora em outro arquivo, podemos criar a nossa stream, nesse caso vamos usar uma como demonstrativo de um upload fake.
```js
import { Readable } from 'node:stream'

class OneToHundredStream extends Readable {
	index = 1
	
	_read() {
		const i = this.index++
		
		setTimeout(() => {
			if(i > 100) {
				this.push(null)
			} else {
				const buf = Buffer.from(String(i))
				
				this.push(buf)
			}
		}, 1000)
	}
}
```
- A partir da versão 18 do Node, conseguimos utilizar de forma nativa a *Fetch API*, nativamente.
- Dessa maneira, conseguimos fazer uma requisição para a stream, nesse caso adicionamos o código abaixo na stream que fizemos acima:
```js
fetch('http://localhost:3334', {
	method: 'POST',
	body: new OneToHundredStream(),
	duplex: 'half'
})
```
- Como foi dito anteriormente, tudo no *Node* é uma Stream, dessa então dessa maneira o *request e o response* tão são.
- Onde o ***REQUEST*** é uma `readableStream`, nesse caso uma stream de leitura
- E o ***RESPONSE*** é uma `writableStream`, nesse caso uma stream de escrita.
- Dessa maneira, podemos fazer o uso da nossa *stream*, da seguinte maneira:
```js
import http from 'node:http'

const server = http.createServer((req, res) => {
	return req
		.pipe(new OneToHundredStream())
		.pipe(res)
})

server.listen(3334)
```
- Dessa maneira, quando iniciamos o nosso servidor e rodamos o arquivo da stream, recebemos a resposta da stream, em nosso servidor aos poucos.