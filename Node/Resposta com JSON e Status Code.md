___
- Quando devolvemos a resposta com o `send`, ela volta em formato de texto.
- Mas também podemos devolver nossas repostas em formato `JSON`, e para fazermos isso, no lugar de usarmos o método `send`, usamos o método `JSON`, da seguinte maneira:
```ts
app.post("/products", (request, response) => {
	const { name, price } = request.body

	response.json({name, price})
})
```
- Podemos também devolver `status code`, de maneira bem simples. É só adicionarmos o método `status` e passar como parâmetro para ele o código que queremos que seja informado quando essa requisição for concluida, deixando o nosso código da seguinte maneira:
```ts
app.post("/products", (request, response) => {
	const { name, price } = request.body

	response.status(201).json({name, price})
})
```