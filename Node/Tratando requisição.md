___
- Para tratar uma requisição, voltamos ao nosso controller, e fazemos da seguinte maneira:
```ts
create(request: Request, response: Response) {
	const { name, price } = request.body

	if(!name || !price) {
		throw new AppError("Nome e preço do produto são obrigatórios!")
	}
}
```
- Agora se o usuário não nos enviar os dados que pedimos, ele irá receber um erro.