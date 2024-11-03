___
- Para testar o [[Criando relacionamento|relacionamento]], vamos fazer uma nova rota com o método `post`;
```ts
app.post("/modules", async (request: Request, response: Response) => {

	const { name, course_id } = request.body

	await knex("course_modules").insert({ name, course_id})

	return response.status(201).json()
})
```
- No `Insomnia`, vamos criar a rota para teste e mandar a seguinte informação no corpo como JSON
```json
{
	"name": "Introdução a Banco de Dados",
	"course_id": 12
}
```
- E agora vamos criar uma rota para listar os módulos
```ts
app.get("/modules", async (request: Request, response: Response) => {
	const modules = await knex("course_modules").select()

	return response.json(modules)
})
```
- Caso tentarmos cadastrar um módulo para um curso de `id` inexistente, vai permitir, pois é padrão do SQLite, então precisamos deixar isso de maneira explicita, para isso voltamos ao arquivo `knexfile.ts` e adicionamos o código a seguir, após a parte de `connection`
```ts
pool: {
	afterCreate: (connection: any, done: any) => {
		connection.run("PRAGMA foreign_keys = ON")
		done()
	},
},
```
- Após isso, o comportamento citado antes não vai ser mais possível;