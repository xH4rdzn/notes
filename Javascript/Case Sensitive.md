___
- Quando uma linguagem de programação é `case-sensitive` significa que ela é sensível a letras maiúsculas e minúsculas.
- Por exemplo -> "Igor" é considerado diferente de "igor".
```js
var product = "Teclado Mecânico"

var Product = "Mouse Gamer"
```
- Mesmo tendo o mesmo nome, por ter diferenças entre maiúsculas e minúsculas são consideradas variáveis diferentes.
- Se tentarmos fazer uma declaração de uma variável já existente, ele irá sobrescrever o valor da que já existe:
```js
var product = "Teclado Mecânico"

var product = "Fone sem fio"

console.log(product) // Retorna Fone sem fio
```
