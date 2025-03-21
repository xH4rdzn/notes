___
- O método `map()`, chama a função callback recebida por parâmetro para cada elemento do Array original, em ordem, e constrói um novo array com base nos retornos de cada chamada. E no final, devolve um novo array.
- Exemplo:
```js
const products = ["Teclado", "Mouse", "Monitor"]

// Percorrendo os itens do array
products.map((product) => {
	console.log(product)
})

// Sintaxe reduzida
products.map((product) => console.log(product))

// Utilizando o novo objeto retornado
const formatted = products.map((product) => {
	return product.toUpperCase()
})

// Exibindo o novo array
console.log(formatted)

// Outro exemplo
const formatted = products.map((product) => {
	return {
		id: Math.random(),
		description: product,
	}
})


```