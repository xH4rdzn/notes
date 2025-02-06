___
- Agora podemos criar um método para listar todos os produtos cadastrados, para isso vamos utilizar o método `index`, e fazemos como no exemplo abaixo:
```ts
async index(request: Request, response: Response, next: NextFunction) {

	try {
		const products = await knex<ProductsRepository>("products")
		.select()
		.orderBy("name")

		return response.json(products)
	} catch(error) {
		next(error)
	} 
}
```
- Podemos também deixar disponível nessa consulta o usuário pesquisar pelo nome, para fazer isso modificamos o método `index`, para:
```Ts
async index(request: Request, response: Response, next: NextFunction) {

	try {
		const { name } = request.query
		const products = await knex<ProductsRepository>("products")
		.select()
		.whereLike("name", `%${name ?? ""}%`)
		.orderBy("name")

		return response.json(products)
	} catch(error) {
		next(error)
	} 
}
```