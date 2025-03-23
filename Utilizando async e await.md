___
- Já aprendemos a utilizar o [[Usando o fetch|fetch com o then]], agora vamos ver como podemos fazer isso utilizando o `async`e `await`;
```js
async function fetchProducts() {
	const response = await fetch("http://localhost:3333/products")
	const data = await response.json()
	console.log(data)
}
```