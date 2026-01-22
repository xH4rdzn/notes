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