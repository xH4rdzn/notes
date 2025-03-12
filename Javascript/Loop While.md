___
- **WHILE** -> repete até que a condição seja verdadeira;
```js
let execute = true

while(execute) {
	// Código a ser repetido
}
```
- Exemplo:
```js
let execute = true

while(execute) {
	let response = window.prompt("Deseja continuar 1(SIM) ou 2(NÃO)")

	if(response === "2") {
		execute = false
	}
}

console.log("Segue o fluxo...")
```

