___
- Em nosso arquivo de `routes.js`, vamos adicionar um novo objeto:
```js
{
	method: 'PUT',
	path: buildRoutePath('/users/:id')
	handler: (req, res) => {
		const { id } = req.params
		const { name, email } = req.body
		
		database.update('users', id, {name, email})
		
		return res.writeHead(204).end()
	}
}
```
- Agora em nosso arquivo `database.js`, vamos criar o método abaixo:
```js
update(table,id, data) {
	const rowIndex = this.#database[table].findIndex(row => row.id === id)
	
	if(rowIndex > -1) {
		this.#database[table][rowIndex] = { id, ...data }
		this.#persist()
	}
}
```