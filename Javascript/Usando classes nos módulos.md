___
- Podemos também exportar classes:
```js
export class Calc {
	sum (a, b) {
		return a + b
	}

	multiply (a, b) {
		return a * b
	}
}
```
- E agora importamos da seguinte maneira:
```js
import { Calc } from './calc.js'
```
- E como ela é uma classe precisamos fazer uma instancia dela
```js
const calc = new Calc()
```
- E agora usamos da seguinte maneira:
```js
console.log(calc.sum(4,6))
```