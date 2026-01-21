___
- Como nossa aplicação pode ter várias rotas, precisamos separar elas, para não ficar uma bagunça em apenas um único arquivo.
- Dentro da nossa pasta `src`, vamos criar o arquivo `routes.js`e dentro desse arquivo vamos seguir como no exemplo abaixo:
```js
import { Database } from './database.js'
import { randomUUID } from 'node:crypto'

const database = new Database()

export const routes = [
	{
		method: 'GET',
		path: '/users',
		handler: (req, res) => {
			const users = database.select('users')
			
			return res.end(JSON.stringify(users))
		}
	},
	{
		method: 'POST',
		path: '/users',
		handler: (req, res) => {
			const { name, email } = req.body
			
			const user = {
				id: randomUUID(),
				name,
				email,
			}
			
			database.insert('users', user)
			
			return res.writeHead(201).end()
		}
	}
]
```
- Agora dentro do nosso arquivo `server.js`, vamos fazer da seguinte maneira:
```js
const server = http.createServer(async (req, res) => {
	const { method, url } = req
	
	await json(req, res)
	
	const route = routes.find(route => {
		return route.method === method && route.path === url
	})
	
	if (route) {
		return route.handler(req, res)
	}
	
	return res.writeHead(404).end()
})

server.listen(3333)
```
- Dessa maneira, para adicionar uma nova rota, precisamos apenas adicionar ela no arquivo `routes`, pois já vai estar adicionada em nossa aplicação.