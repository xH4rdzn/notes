___
- O método `find()`, retorna o valor do primeiro elemento do array que satisfazer a condição. Caso contrário, retorna `undefined`;
```js
const values = [5, 12, 8, 130, 44]

const found = values.find((value) => value > 10)
console.log(found) // Retorna 12 que é o primeiro elemento que satisfaz a condição passada;

// Exemplo com objetos
const fruits = [
	{name: "apples", quantity: 23},
	{name: "oranges", quantity: 25},
	{name: "bananas", quantity: 52},
]

const result = fruits.find((fruit) => fruit.name === "bananas")
```