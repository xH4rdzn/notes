___
- Para exibirmos os logs de um pedido, ou seja os estados no qual esse pedido já passou, alteramos o método `show` do controller de `deliveryLogsController`, deixando o da seguinte maneira:
```Ts
async show(request: Request, response: Response) {
	const paramsSchema = z.object({
		delivery_id: z.string().uuid(),
	})

	const { delivery_id } = paramsSchema.parse(request.params)

	const delivery = await prisma.delivery.findUnique({
		where: {
			id: delivery_id,
		},
		include: {
			logs: true,
			user: true,
		}
	})

	if(request.user?.role === "customer" && request.user.id !== delivery?.userId) {
		throw new AppError("The User can only view their deliveries", 401)
	}

	

	return response.json(delivery)
}
```
- Se quisermos mostrar alguns dados apenas e não todos, podemos fazer como no exemplo abaixo para o usuário:
```ts
include: {
	user: {
		select: {
			id: true,
			name: true,
		}
	}
}
```