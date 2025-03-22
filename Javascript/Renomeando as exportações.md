___
- Para podermos renomear as exportações, temos que fazer da seguinte maneira:
```js
function sum(a, b) {
	return a + b
}

function multiply(a, b) {
	return a * b
}

export { sum as sumTwoNumbers , multiply as multiplyTwoNumbers}
```
- E agora para importarmos essas funções usamos os nomes na qual foi dado no `as`
```js
import { sumTwoNumbers } from './calc.js'
```
- E a usamos com o nome de sua importação
```js
console.log(sumTwoNumbers(4, 6))
```
