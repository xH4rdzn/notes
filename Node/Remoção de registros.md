___
- Agora para podermos apagar um registro do nosso banco de dados precisamos recuperar o parâmetro que veio na rota:
```js
if(route) {
	const routeParams = req.url.match(route.path)

	req.params = { ...routeParams.groups}

	return route.handler(req,res)
}
```
- Agora em nosso arquivo de rotas, como temos acesso ao `req`, fica mais fácil para recuperar o parâmetro que veio pela rota.
```js
{
	method: 'DELETE',
	path: buildRoutePath('/users/:id')
	handler: (req, res) => {
		const {id} = req.params
		
		database.delete('users', id)
		
		return res.writeHead(204).end()
	}
}
```
- Agora no arquivo `database.js`, vamos adicionar o seguinte método:
```js
delete(table, id) {
	const rowIndex = this.#database[table].findIndex(row => row.id === id)
	
	if(rowIndex > -1) {
		this.#database[table].splice(rowIndex,1)
		this.#persist()
	}
}
```