___
- Agora vamos criar um método para atualizar os dados do produto, esse método chamamos de `update`e fazemos da seguinte maneira:
```ts
async update(request: Request, response: Response, next: NextFunction) {

	try{

		return response.json({ message: "Ok"})
	} catch(error) {
	
	}
}
```
- Agora vamos em nosso arquivo `productsRoutes`e adicionamos:
```ts
productsRoutes.put('/:id', productsController.update)
```
- Precisamos receber o id para saber qual o produto vamos alterar
- Esse `id`, chega como uma `string`, então precisamos tratar ela, para que vire um número. Caso estejamos usando um `id`numérico, para fazer isso seguimos o exemplo:
```TS
const id = z
.string()
.transform((value) => Number(value))
.refine((value) => !isNaN(value), { message: "id must be a number"})
.parse(request.params.id)
```
- Como estamos atualizando um produto, precisamos mandar as informações novas, para isso podemos também validar o corpo da requisição, para isso também vamos utilizar o `zod`, como no exemplo:
```ts
const bodySchema = z.object({
	name: z.string().trim().min(6),
	price: z.number().gt(0)
})

const { name, price } = bodySchema.parse(request.body)
```
- Agora para poder fazer a alteração no banco de dados, fazemos como no exemplo abaixo:
```Ts
await knex<ProductsRepository>("products").update({ name, price, updated_at: knex.fn.now() }).where({ id })
```