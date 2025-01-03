___
- Ainda no `DeliveryLogsController`, vamos agora criar o método `show`, que vai ser usado para exibir os detalhes do pedido:
```ts
async show(request: Request, response: Response) {
	const paramsSchema = z.object({
		delivery_id: z.string().uuid(),
	})

	const { delivery_id } = paramsSchema.parse(request.params)

	const delivery = await prisma.delivery.findUnique({
		where: {
			id: delivery_id,
		}
	})

	return response.json(delivery)
}
```
- E agora vamos criar uma rota, para esse método do controller, no arquivo `deliveryLogsRoutes.ts`, vamos adicionar o seguinte:
```ts
deliveryLogsRoutes.get(
	"/:delivery_id/show",
	ensureAuthenticated,
	verifyUserAuthorization(["sale", "customer"]),
	deliveryLogsController.show
)
```
- Agora precisamos garantir que o usuário consiga ver apenas os pedidos feito por ele, para isso voltamos ao nosso controller e vamos alterar o método `show`
```ts
async show(request: Request, response: Response) {
	const paramsSchema = z.object({
		delivery_id: z.string().uuid(),
	})

	const { delivery_id } = paramsSchema.parse(request.params)

	const delivery = await prisma.delivery.findUnique({
		where: {
			id: delivery_id,
		}
	})

	if(request.user?.role === "customer" && request.user.id !== delivery?.userId) {
		throw new AppError("The User can only view their deliveries", 401)
	}

	

	return response.json(delivery)
}
```