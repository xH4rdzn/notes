___
- Para remover um registro do banco de dados, no *controller*, usamos o método **remove**, ficando da seguinte maneira:
```Ts
async remove(request: Request, response: response, next: NextFunction) {

	try {
		const id = z
		.string()
		.transform((value) => Number(value))
		.refine((value) => !isNaN(value), { message: "id must be number"})
		.parse(request.params.id)


		await knex<ProdcutRepository>("products").delete().where({ id })
	} catch(error) {
		next(error)
	}

}
```
- Agora precisamos disponibilizar esse método em uma rota, para isso vamos em nosso arquivo `productsRoutes`e adicionamos a rota da seguinte maneira:
```Ts
productsRoutes.delete("/:id", productsController.remove)
```
- Porém se passarmos um `id` de um produto que não existe, ele vai retornar um status code de *ok*;
- Agora precisamos validar se esse produto existe para ser apagado, assim como também precisamos fazer isso para o método de [[Atualizando protudos|atualizar os produtos]];
- Para fazer isso, antes da operação de apagar ou atualizar no banco de dados, fazemos um `select`
```Ts
const product = await knex<productRepository>("products").select().where({ id }).first()
```
- Após fazer isso, fazemos uma verificação se o produto existe ou não:
```ts
if(!product) {
	throw new AppError("Product not found")
}
```
- Podemos aplicar a mesma lógica para o método de [[Atualizando protudos|atualizar os produtos]]
