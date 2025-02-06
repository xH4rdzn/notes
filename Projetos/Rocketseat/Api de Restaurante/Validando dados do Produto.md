___
- Agora vamos criar uma rota para cadastrar os produtos;
- Então no Insomnia, criamos uma rota do tipo `POST`e passamos os seguintes dados no corpo da requisição:
```json
{
	"name": "Porção de batata frita",
	"price": 59.90
}
```
- Agora precisamos criar essa rota dentro da nossa aplicação, para isso vamos no `productsController.ts`e criamos o método `create`, como no exemplo abaixo:
```ts
async create(request: Request, response: Response, next: NextFunction) {
	try {
		const { name, price } = request.body

		return response.status(201).json({ name, price})
	} catch (error) {
		next(error)
	}
}
```
- Agora vamos no arquivo `productsRoutes`e adicionamos a rota no qual vai chamar esse método no controller:
```Ts
productsRoutes.post('/', productsController.create)
```
- Porém se esquecermos de mandar o nome ou o preço, a rota vai funcionar da mesma maneira;
- Então vamos validar os dados com o `zod`, para isso vamos adicionar o seguinte no `controller`
```ts
async create(request: Request, response: Response, next: NextFunction) {
	try {
		const bodySchema = z.object({
			name: z.string().trim().min(6),
			price: z.number().gt(0, { message: "O valor deve ser maior que 0"})
		})

		const { name, price } = bodySchema.parse(request.body)

		
	} catch(error) {
		next(error)
	}

}
```
- Desta maneira o `zod`valida se estamos recebendo as informações que precisamos, caso contrário ele irá lançar uma exceção.
