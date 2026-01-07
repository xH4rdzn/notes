___
- Uma requisição HTTP é composta principalmente por duas coisas:
	- Método HTTP
	- URL
- Conseguimos recuperar essas informações a partir de `request`, ou como chamamos `req`, como no exemplo abaixo:
```js
const server = http.createServer((req, res) => {
	const { method, url } = req
	
	console.log(method, url)
})
```

### Métodos HTTP
- Os métodos mais comuns HTTP, são os:
	- GET
	- POST
	- PUT
	- PATCH
	- DELETE
- Onde:
- ***`GET`*** -> Buscar uma informação do back-end
- ***`POST`*** -> Criar um recurso no back-end
- ***`PUT`*** -> Atualizar um recurso no back-end
- ***`PATCH`*** -> Atualizar uma informação especifica de um recurso no back-end
- ***`DELETE`*** -> Deletar um recurso do back-end
- Então dessa maneira podemos ter endpoints na mesma ***URL*** e o que vai diferenciar entre elas é o método HTTP
```js
const server = http.createServer((req, res) => {
	const { method, url } = req
	
	if(method === 'GET' && url === '/users') {
		return res.end('Listagem de usuários')
	}
	
	if (method === 'POST' && url === '/users') {
		return res.end('Criação de usuário')
	}
})
```