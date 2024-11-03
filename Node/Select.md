___
- Para usarmos o método `select` do `knex`, primeiramente precisamos de uma rota do tipo `get`;
```ts
app.get("/courses", async (request: Request, response: Response) => {
	const courses = await knex("courses").select()

	reponse.json(courses)
})
```
- Podemos também usar o `raw`, para escrever o SQL de forma manual
```ts
app.get("/courses", async (request: Request, response: Response) => {
	const courses = await knex.raw("SELECT * FROM courses")

	reponse.json(courses)
})
```
- Podemos também ordenar usando o método `orderBy()`, que recebe como parâmetro por qual coluna queremos ordenar:
```ts
app.get("/courses", async (request: Request, response: Response) => {
	const courses = await knex("courses").select().orderBy("name")

	reponse.json(courses)
})
```
- E se quisermos mudar a ordem para decrescente, passamos da seguinte maneira:
```ts
app.get("/courses", async (request: Request, response: Response) => {
	const courses = await knex("courses").select().orderBy("name", "desc")

	reponse.json(courses)
})
```