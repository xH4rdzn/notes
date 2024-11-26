___
- Após criarmos a [[Criando a Tabela de Perguntas|tabela de perguntas]], podemos criar a rota `create`em nosso controller de perguntas, deixando o nosso código da seguinte maneira:
```ts
async create(request: Request, response: Response) {
	const { title, content, user_id } = request.body

	await prisma.question.create({
		data: {
			title,
			content,
			userId: user_id
		},
	})
	
}
```
- E em nossa requisição mandamos um um `JSON`, com os seguintes dados:
```json
{
	"title": "Prisma ORM",
	"content": "Como inserir no banco de dados com o Prisma",
	"user_id": "auiheduahduahd"
}
```
- Desta maneira a questão enviada será salva no banco de dados.