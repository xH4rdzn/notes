___
- Conseguimos criar propriedades dentro das classes, como demostrado no exemplo abaixo:
```js
class Product {
	constructor(name) {
		this.name = name
	}
}
```
- Com o uso da keyword `this`, dizemos que nessa classe existe uma propriedade, no exemplo acima `name`, mas podemos criar qualquer propriedade que desejarmos;
- E também podemos acessar essas propriedades como no exemplo a seguir:
```js
const product = new Product("Teclado")
console.log(product.name) // Retorna -> Teclado
```