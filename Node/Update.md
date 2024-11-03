___
- Para atualizar um registro, com os métodos do `knex`, vamos criar uma rota utilizando o método `put`, como no exemplo abaixo:
```ts
app.put("/courses/:id", async (request: Request, response: Response) => {
	const { name } = request.body
	const { id } = request.params

	// Método update para atualizar dados
	await knex("courses").update({ name }).where({ id })

	return response.json()
})
```