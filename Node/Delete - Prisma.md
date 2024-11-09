___
- Para remover um registro com o prisma é bem simples e bem parecido com o método [Update](./Update%20-%20Prisma.md), só muda que não passamos um `request.body`, e usamos o método `delete`, do prisma;
- Deixando o nosso código da seguinte maneira:
```ts
async remove(request: Request, response: Response) {
	const { id } = request.params

	await prisma.question.delete({
		where: {
			id,
		}
	})

	return response.json()
}
```