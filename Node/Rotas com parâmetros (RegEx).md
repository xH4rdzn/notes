___
- Agora precisamos fazer com que seja substituido no nosso URL, pelo parâmetros, para isso vamos acrescentar
```js
export function buildRoutePath(path) {
	const routeParametersRegex = /:([a-zA-z])/g
	
	const pathWithParams = path.replaceAll(routeParametersRegex, '([a-z0-9\-_]+)')
	
	const pathRegex = new RegExp(`^${pathWithParams}`)
	
	return pathRegex
}
```
- Agora em nosso servidor, vamos fazer a seguinte alteração:
```js
const server = http.createServer(async (req, res) => {
	const { method, url } = req
	
	await json(req, res)
	
	const route = routes.find(route => {
		return route.method === method && route.path.test(url)
	})
	
	if (route) {
		return route.handler(req, res)
	}
	
	return res.writeHead(404).end()
})

server.listen(3333)
```
- E nosso arquivo onde está as nossas rotas, podemos fazer da seguinte maneira:
```js
import { Database } from './database.js'
import { randomUUID } from 'node:crypto'

const database = new Database()

export const routes = [
	{
		method: 'GET',
		path: buildRoutePath('/users'),
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
	},
	{
		method: 'DELETE',
		path: buildRoutePath('/users/:id'),
		handler: (req, res) => {
			return res.end()
		},
	}
	
]
```
- Agora voltando para o nosso arquivo `server.js`, vamos adicionar a parte de rotas para:
```js
if(route) {
	const routeParams = req.url.match(route.path)
}
```
- Voltando no arquivo da nossa ***REGEX***, vamos adicionar:
```js
const pathWithParams = path.replaceAll(routeParametersRegex, '(?<$1>[a-z0-9\-_]+)')
```