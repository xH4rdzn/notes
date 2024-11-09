___
- Além de listar todos os registros, podemos fazer uma pesquisa, por algum parâmetro;
- Para fazer  isso vamos usar os `Query Parameters`;
- Dentro do método [FindMany](./FindMany.md), podemos passar um objeto `{}`, com a clausula `where`, para podermos aplicar o filtro, como no exemplo abaixo:
```ts
async index(request: Request, response: Response) {
	const questions = await prisma.question.findMany({
		where: {
			title: {
				contains: request.query.title?.toString(),
				mode: "insensitive",
			}
		}
	})
}
```
- Dentro do `title`, usamos a propriedade `contains`, para poder achar um valor aproximado, se passarmos apenas o `title`, ele vai procurar por registros exatamente igual;
- E para ele não fazer diferença entre maiúsculo e minúsculo, usamos a propriedade `mode`, e passamos o valor `"insensitve"`;
- Podemos também aplicar a propriedade `orderBy`, para ordenar os registros; ficando da seguinte maneira:
```ts
async index(request: Request, response: Response) {
	const questions = await prisma.question.findMany({
		where: {
			title: {
				contains: request.query.title?.toString(),
				mode: "insensitive",
			},
		},
		orderBy: {
				title: "desc"
			}
	})
}
```