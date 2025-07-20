___
- Dentro de um *array*, podemos por diversos tipos de dados, como:
```js
const myArray = [
 "String",
 15, // Número
 true, // Boolean
 function () {
	console.log('Função dentro do array')	
},
{
	name: "Igor",
	email: "igor@email.com"
}
]
```
- Como vimos acima, podemos guardar todos os tipos de dados dentro de um array;
- Para executarmos uma função que está dentro de um array, podemos fazer como no exemplo abaixo:
```js
myArray[3]()
```
- E para objetos, podemos fazer da seguinte maneira:
```js
console.log(myArray[4].name)
```
