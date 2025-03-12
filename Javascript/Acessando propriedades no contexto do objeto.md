___
- Podemos usar as propriedades do objeto em outra propriedade, como no exemplo abaixo
```js
const user = {
	name: "Igor",
	messge: function () {
		console.log(``Olá ${user.name})
	}
}
```
- Podemos fazer a referência como na maneira acima, ou usar a keyword `this`
```js
const user = {
	name: "Igor",
	messge: function () {
		console.log(``Olá ${this.name})
	}
}
```
- Para usar o `this`, **não podemos usar a arrow function**;
- 