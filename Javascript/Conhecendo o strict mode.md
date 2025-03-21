___
- O *stric mode* (modo estrito) ativando esse modo, os erros que eram silenciosos passa a gerar exceções no Javascript;
```js
// Desta maneira não irá gerar erro, ele disponibiliza a variável de maneira global;
function showMessage() {
	personName = "Igor Coelho"

	console.log("Olá", personName)
}

// Usando o modo `stric`, ele já irá gerar um erro
function showMessage() {
	"use strict"
	personName = "Igor Coelho"

	console.log("Olá", personName)
}
```
- Para usarmos no escopo global, basta colocarmos o `"use stric"`no inicio do documento;