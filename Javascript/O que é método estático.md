___
- Métodos estáticos são métodos que não precisam de uma instancia da classe para serem utilizados;
- Para definirmos um método estático, usamos a keyword `static`, como demostrado no exemplo abaixo:
```js
class User {
	static showMessage() {
		console.log("Essa é uma messagem")
	}
}
```
- Para usarmos o método basta usarmos o nome da classe e o método que queremos:
```js
User.showMessage()
```
- Só devemos tomar cuidado para não passar argumentos do contexto da classe para um método estático, pois se não fizemos a instancia dela, o valor será `undefined`;
