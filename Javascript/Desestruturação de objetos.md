___
- Como vimos anteriormente podemos fazer a [[Desestruturação de array]], e também podemos fazer isso em objetos;
- Como no exemplo abaixo:
```js
const product = {
	description: "Teclado",
	price: 150
}

// Desestruturando o objeto
const { description, price } = product

// Usando as variáveis
console.log("Descrição:", description)
console.log("Preço:", price)
```
- Podemos usar isso em funções também, como no exemplo abaixo:
```js
function newProduct({description, price}) {
	console.log("Descrição:", description)
	console.log("Preço:", price)
}

// Usando a função com parâmetros desestruturados
newProduct({
	price: 70,
	description: "Mouse",
})
```