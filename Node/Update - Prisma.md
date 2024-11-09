___
- Para atualizar os registros usamos o método `update` do prisma;
- Passamos o novo conteúdo do registro através do `request.body`;
- E recuperamos o `id`, do registro que queremos mudar através do `request.params`;
- Deixando o nosso controller da seguinte forma;
```ts
async update(request: Request, response: Reponse) {
	const { id } = request.params
	const { title, content } = request.body

	await prisma.question.update({
		data: {
			title,
			content
		},
		where: {
			id,
		}
	})
}
```
- No exemplo acima, fazer um `update`, em um registro que é recebido como parâmetro de rota;
