___
- Agora quando quisermos passar o middleware, apenas para uma rota especifica, fazemos da seguinte maneira:
```ts
app.post("/products", myMiddleware, (request, response) => {
	// código aqui
})
```
- Passamos o middleware, após o `endereço` da rota, como no exemplo acima.