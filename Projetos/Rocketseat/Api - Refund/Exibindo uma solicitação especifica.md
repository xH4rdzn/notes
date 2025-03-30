___
- Agora podemos criar um novo método para poder exibir uma solicitação especifica, para isso vamos criar o método `show`em nosso controller:
```ts
async show(request: Request, response: Response) {
	const paramsSchema = z.object({
		id: z.string().uuid(),
	})

	const { id } = paramsSchema.parse(request.params)

	const refund = await prisma.refunds.findFirst({
		where: { id },
		include: { user: true}
	})

	return response.json(refund)
}
```
- E agora adicionamos essa funcionalidade em nossas rotas, para isso vamos no arquivo `refundsRoutes`, e adicionamos a rota da seguinte maneira:
```ts
refundsRoutes.get(
	":/id",
	verifyUserAuthorization(["employee", "manager"])
	refundsController.show
)
```