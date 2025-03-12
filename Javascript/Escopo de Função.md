___
- As funções podem ser chamadas antes de ser declaradas, isso é o [[Hoisting]], como demostrado no exemplo abaixo:
```js
showMessage("Olá, Igor!")

function showMessage(message) {
	console.log(message)
}
```
- Conseguimos também criar uma função dentro de outra função, como no exemplo abaixo:
```js
function showMessage(message) {
	console.log(message)
	endLine()

	function endLine() {
		console.log('----------')
	}
```
- Mas se tentarmos chamar a função `endLine`fora da função `showMessage`, irá dar error, pois essa função só existe no escopo da função `showMessage`;
