___
- Como vimos anteriormente, podemos [[Renomeando as exportações|renomear no momento da exportação]], mas também podemos renomear no momento da importação;
- Para isso também usamos o `as`, para renomear
```js
import { sum as s } from './calc.js'
```
- E agora usamos a função importada através do nome dado:
```js
console.log(s(4,6))
```
