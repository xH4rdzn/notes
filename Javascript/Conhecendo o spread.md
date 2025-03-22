___
- `Spread` (espalhar), permite que um objeto iterável, como uma expressão de array ou uma string seja expandido para ser usado onde zero ou mais argumentos
```js
const numbers = [1, 2, 3]
console.log(numbers)

// Spread
console.log(...numbers)

// Usando um array de objetos
const data = [
	{
		name: "Igor",
		email: "igor@email.com",
		avatar: "i.png"
	},
	{
		name: "Lucas",
		email: "lucas@email.com",
		avatar: "l.png"
	}
]

// Exibindo o array de objetos
console.log(data)


// Devolvendo os objetos separados;
console.log(...data)
```