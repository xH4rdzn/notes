___
- Para podermos criar um módulo, usamos a keyword `export`no módulo no qual queremos importar:
```js
// Exportando uma função

export function sum(a, b) {
	return a + b
}
```
- Ou também podemos exportar da seguinte maneira:
```js
// Outra maneira de exportar

function sum(a, b) {
	return a + b
}

function multiply(a, b) {
	return a * b
}

export { sum, multiply}
```
- E agora para podermos usarmos esses módulo usamos a keyword `import`
```js
// Importando um módulo
import { sum } from './calc.js'
```
- Ou então podemos importar mais de um módulo que vem do mesmo arquivo:
```js
// Importando mais de um módulo do mesmo arquivo
import { sum, multiply } from './calc.js'
```
- Se tivermos usando módulos em projeto com HTML, CSS e JS, ao indexarmos o javascript com o HTML, precisamos adicionar a propriedade `type` na tag `script`
```html
<script type="module" src="main.js"></script>
```