___
- Agora podemos criar uma rota para poder listar as solicitações, voltamos ao `refundsController`e vamos adicionar um novo método:
```ts
async index(request: Request, response: Response) {
	return response.json({message: "ok"})
}
```
- Agora no arquivo `refundsRoutes`, precisamos disponibilizar essa rota, para isso adicionamos:
```ts
refundsRoutes.get(
"/",
verifyUserAuthorization(["manager"]),
refundsController.index
)
```
- Agora podemos criar no `Insomnia`para testar o endpoint;