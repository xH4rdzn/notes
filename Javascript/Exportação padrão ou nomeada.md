___
- Também podemos exportar módulos por padrão, neste caso usamos a keyword `default`
```js
export default function sum(a, b) {
	return a + b
}
```
- E agora para usarmos essa função não usamos mais `{}`, no momento de sua importação, podemos simplesmente fazer desta maneira:
```js
import sum from './calc.js'
```
- Chamamos isso de *Exportação padrão*. É a função fornecida pelo módulo;
- Outra diferença para as `default export`, podemos dar o nome que quisermos no momento de sua importação
```js
export default function sum(a, b) {
	return a + b
}

// batata é a função sum, que é exportada por padrão
import batata from './calc.js'
```
- E quando usamos as `{}`, chamamos de *Exportação nomeada* ou *named export*. São importadas pelo seu próprio nome de exportação