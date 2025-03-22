___
- Como vimos anteriormente [[Criando os módulos|podemos exportar módulos]] de maneira separadas e importar ela de maneira separada também;
- Mas também podemos importar todas as funções que um módulo exporta, para isso fazemos da seguinte maneira:
```js
// Importando tudo do módulo
import * as calc from './calc.js'
```
- `as` -> usamos para dar um nome para o arquivo no qual importamos tudo;