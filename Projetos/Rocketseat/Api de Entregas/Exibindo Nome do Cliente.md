___
- Quando criamos o método de [[Listar entregas|listar]] as entregas, vimos que ele devolve apenas o `ID`do usuário, mas podemos também devolver outros dados.
- Para fazer voltamos ao nosso controller e dentro do método `findMany`, acrescentamos:
```ts
async index(request: Request, response: Response) {
	const deliveries = await prisma.delivery.findMany({
		includes: {
			user: {
				select: {
					name: true,
					email: true,
				}
			}
		}
	})

	return response.json(deliveries)
}
```
- Desta maneira facilita, para ver que o pedido foi enviado para *tal cliente*;
