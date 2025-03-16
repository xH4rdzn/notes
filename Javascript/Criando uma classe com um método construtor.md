___
- Para criarmos uma classe podemos fazer como no exemplo a seguir:
```js
class Person {
	constructor(name){
		console.log("Olá", name)
	}
}
```
- Normalmente para definir os nomes das classes usamos o *Pascal Case*.
- *Nota-se que podemos passar parâmetros para o método construtor*;
- Para instanciarmos uma classe podemos fazer da seguinte maneira:
```js
const person = new Person()
```
- Toda vez que instanciamos uma classe o método construtor é executado;