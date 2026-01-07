___
- Para podermos criarmos um projeto em Node.js, navegamos até a pasta onde desejamos que os arquivos do nosso projeto fiquem, e depois usamos o comando abaixo:
```zsh
npm init -y
```
- Após isso será gerado um arquivo ****`package.json`***.
- Nesse arquivo, vamos adicionar a seguinte linha:
```json
"type": "module"
```
- Agora podemos criar uma pasta com o nome de ***`src`*** e criar o arquivo `server.js`e dentro dele podemos fazer as importações da seguinte maneira:
```js
import http from "node:http"
```
- Agora podemos criar o nosso servidor, com node puro, seguindo o exemplo abaixo:
```js
const server = http.createServer((request, response) => {
	return response.end('Hello World')
})

server.listen(3333)
```