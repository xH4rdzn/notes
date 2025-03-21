___
- O método `filter()`cria um novo array com todos os elementos que passaram na condição.
```js
const words = ["javascript", "HTML", "CSS", "Web"]

// Devolvendo um novo array com os itens que atendem a condição
const result = words.filter((word) => word.length > 3)
console.log(result)

// Outro exemplo
const products = [
	{description: "Teclado", price: 150, promotion: true},
	{description: "Mouse", price: 70, promotion: false},
	{description: "Monitor", price: 900, promotion: true},
]

const promotion = products.filter((product) => product.promotion === true)

console.log(promotion)
```