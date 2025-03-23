___
- Agora vamos fazer uma função para poder listar um produto especifico
```js
async function fetchProductById(id) {
	const response = await fetch(`http://localhost:3333/products/${id}`)
	const data = await response.json()
}
```
- Agora quando quisermos um produto específico, usamos da seguinte maneira:
```js
fetchProductById("3")
```
