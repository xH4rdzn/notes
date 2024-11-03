___
- Para poder passar um `route params`, fazemos da seguinte maneira:
```ts
app.get("/products/:id", (request, response) => {
	// Código aqui
})
```
- Os `route params`, são obrigatórios.
- Conseguimos recuperar os `route params`, da seguinte maneira:
```ts
app.get("/products/:id", (request, response) => {
	const { id } = request.params
})
```
- E podemos usar esse parâmetro no nosso código.
- Podemos passar mais de um `route params`.
```ts
app.get("/products/:id/:user", (request, response) => {
	const { id, user } = request.params
})
```
