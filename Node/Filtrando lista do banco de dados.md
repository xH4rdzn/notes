___
- Agora para filtrar em nosso banco de dados, vamos precisar alterar o método `select`, que criamos:
```js
select(table, search) {
	let data = this.#database[table] ?? []
	
	if (search) {
		data = data.filter(row => {
			return Object.entries(search).some(([key, value]) => {
				return row[key].includes(value)
			})
		})
	}
}
```
- E em nosso arquivo de rotas, precisamos alterar o método `GET`, para poder receber os `query params`:
```js
{
	method: 'GET',
	path: buildRoutePath('/users'),
	handler: (req, res) => {
		const { search } = req.query
		
		const users = database.select('users', search ? {
			name: search,
			email: search,
		} : null)
	}
}
```
- Se tivermos mais de um parâmetro para filtro, podemos fazer a validação da seguinte maneira:
```js
const { title, description } = req.query

let filters = null

if (title || description) {
	filters = {}
	
	if (title) filters.title = title
	if (description) filters.description = description
}

const tasks = database.select('tasks', filters)
```
- Dessa maneira, funciona sem os filtros, passando apenas um deles ou passando os dois filtros.