___
- Para apagar registros, vamos criar uma rota com o método `delete`, e vamos usar um método do `knex`, como no exemplo abaixo:
```ts
app.delete("/courses/:id", async (request: Request, reponse: Reponse) => {
	const { id } = request.params

	await knex("courses").delete().where({ id })

	return response.json()
})
```