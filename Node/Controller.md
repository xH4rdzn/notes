___
- Vamos separar as ações de cada rota em arquivo que chamamos de `controllers`.
- Para fazer isso vamos seguir os passos abaixo:
1. Dentro da pasta `src`, vamos criar uma pasta com nome de: `controllers`
2. Dentro da pasta `controllers`, vamos criar um arquivo para cada tipo de `controller`, nesse exemplo vamos criar um `controller`, para os produtos então o nome do nosso arquivo vai ser: `ProductsController.ts`
3. Dentro desse arquivo vamos criar ele da seguinte maneira:
```ts
export class ProductsController {}
```
- Existe uma maneira de padronizar os `controllers`
- Os `controllers`, vão ter no máximo 5 métodos, que são:
	- index - GET, para listar vários registros.
	- show - GET, para exibir um registro específico.
	- create - POST, para criar um registro
	- update - PUT, para atualizar um registro
	- remove - DELETE, para deletar um registro
- Se o `controller`, precisar de mais um método, é um sinal que precisamos criar outro `controller` separado para esse outro método.
4. Criamos esses métodos da seguinte maneira:
```ts
import { Request, Response } from "express"

export class ProductsController {

	index(request: Request, response: Response) {
		const { page, limit } = request.query

		response.send(`Página ${page} de ${limit}`)
	}

	create(request: Request, response: Response) {
		const { name, price } = request.query

		response.status(201).json({name, price})
	}

}
```
5.  Agora para usarmos esse controller, voltamos ao arquivo das rotas do `controller` e o importamos
```ts
import { ProductsController } from "../controllers/ProductsController"
```
6. Como ele é uma classe, precisamos fazer uma instância do controller:
```ts
const productsController = new ProductsController()
```
7. E agora para usarmos, fazemos da seguinte maneira:
```ts
productsRoutes.get("/", productsController.index)
productsRoutes.post("/", myMiddleware, productsController.create)
```
