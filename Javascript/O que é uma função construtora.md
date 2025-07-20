___
- Uma função construtora é a que usamos com o operador `new`, que é capaz de fazer a instância de um objeto;
- Como no exemplo abaixo:
```js
function createProduct(name) {
	const product = {}

	product.name = name
	product.details = function () {
		console.log(`O nome do produto é ${this.name}`)
	}

	return product
}
```
- Acima temos uma função construtora, que é uma função que cria um objeto e o retorna;
- Quando estamos fazendo uma instância, estamos fazendo uma nova cópia de um objeto, para fazer isso usamos a keyword `new`;
```js
const product1 = new createProduct("Teclado")
console.log(product1.name)
product1.details()


const product2 = new createProduct("Mouse")
console.log(product2.name)
product2.details()
```
- Eles são cópias, mas são objetos diferentes, são iguais apenas em sua estrutura;
- Quando usamos o `new`, ele cria um novo objeto com a mesma estrutura do construtor que definimos ou da função construtora;
- O *Javascript*, já possui funções construtoras, como nos exemplos abaixo:
```js
let myName = new String("Igor")
console.log(myName) // Retorna um objeto com o texto "Igor"

let price = "40.6".replace(".", "")
console.log(price) // Retorna 406


let date = new Date("2025-1-1")
console.log(date) // retorna um objeto de data, com várias informações

```
