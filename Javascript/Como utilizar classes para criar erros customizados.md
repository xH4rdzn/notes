___
- Podemos usar `class`, para poder fazer tratamento customizados de erros, como no exemplo abaixo:
```js
class MyCustomError {
	constructor(message){
		this.message = "Classe de erro customizada: " + message
	}
}
```
- E usamos essa classe da seguinte maneira:
```js
try {
	throw new MyCustomError("Erro personalizado")
} catch(error) {
	if(error instanceof MyCustomError) {
		console.log(error.message)
	} else {
		console.log("Não foi possível")
	}
}
```
