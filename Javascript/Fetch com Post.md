___
- Até agora só usamos o `fetch()`, para ler em outras palavras com o método `GET`, agora vamos aprender a usar o `fetch()`, com o método `POST`;
```js
const productName = document.getElementById("name")
const productPrice = document.getElementById("price")

fetch("http://localhost:3333/products", {
	method: 'POST',
	headers: {
		"Content-type": "application/json"
	},
	body: JSON.stringify({
		id: new Date().getTime().toString(),
		name: productName.value,
		price: productPrice.value,
	})
})
```
- Seguindo o exemplo acima, conseguimos enviar dados usando o `fetch()`;
