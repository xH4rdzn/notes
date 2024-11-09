___
- Esse método retorna todos os registros encontrados para aquela tabela;
- Abaixo temos um exemplo no qual vamos listar todos os registros da tabela `user`;
```ts
async index(request: Request, response: Response) {
	const users = await prisma.user.findMany()

	return response.json(users)
}
```
- O código acima, deve retornar todos os registros da tabela `user`;
