___
- Agora vamos usar o método `post`, para poder enviar dados para a nossa `api`.
- Com o `express`, usamos o método `post`, da seguinte maneira;
```ts
app.post("/products", () => {
	// código aqui
})
```
- E para enviar dados para a nossa `api`, usamos o formato `JSON`.
- E para recuperar os dados, recuperamos com os mesmos nomes que foram enviados pelo corpo da nossa requisição, em formato `JSON`;
```ts
app.post("products", (request, response) => {
	const { name, price } = request.body
})
```
- Nota-se que recuperamos esses dados de `request.body` e com os mesmos nomes.
- Porém, para podermos enviar dados para uma `api`, precisamos informar como a `api`, vai receber esses dados.
- Para configurar nossa `api`, para receber dados em formato `JSON`, vamos fazer adicionar a seguinte linha no nosso `server.ts`:
```ts
app.use(express.json())
```
- Agora podemos enviar dados para a nossa `api`, no formato `JSON`.