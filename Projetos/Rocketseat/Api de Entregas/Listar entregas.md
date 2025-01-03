___
- Anteriormente, criamos o método de [[Cadastra Entrega|cadastrar as entregas]],agora vamos criar o método de listar as entregas, para isso ainda vamos usar o `DeliveriesController`  e o criamos da seguinte maneira:
```ts
class DeliveriesController {
	async create() {
		// Código
	}

	async index(request: Request, response: Response) {
		const deliveries = await prisma.delivery.findMany()
	
		
		return response.json(deliveries)
	}
}
```
- Precisamos criar uma rota para poder passar esse método, então vamos ao arquivo `deliveriesRoutes`, e adicionamos como no exemplo abaixo:
```ts
deliveriesRoutes.get("/", deliveriesController.index)
```
- Desta maneira já é possível listar os pedidos de um usuário