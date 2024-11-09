___
- Podemos usar esse método para encontrar um registro único;
- Como no exemplo abaixo que vamos pegar um recuperar um registro de usuário:
```ts
async show(request: Request, response: Response) {
	const { id } = request.params

	const user = await prisma.user.findUnique({where: { id } })

	return response.json(user)
}
```
- Agora o `id`, deve ser passado na rota, para poder retornar um usuário em especifico;