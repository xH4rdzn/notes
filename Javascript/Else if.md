___
- Com o `else if`, podemos ter várias condições para ser verificadas, como no exemplo abaixo:
```js
let hour = 11

if (hour <= 12) {
	console.log("Bom Dia!")
} else if (hour > 12 && hour <= 18) {
	console.log("Boa Noite!")
} else {
	console.log("Boa noite!")
}
```
