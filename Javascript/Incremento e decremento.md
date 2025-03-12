___
- Os operadores de incremento e decremento podem ser usados para adicionar ou diminuir mais 1 em uma variável.
- Para incrementar usamos o operador: `++`;
```js
let number = 10

// Incrementa após
console.log(number++)

// Incrementa antes
console.log(++number)
```
- Para fazer o decremento usamos o operador: `--`;
```js
console.log("Decremento após: ", number--)

console.log("Decremento antes: ", --number)
```
- Esses operadores serve para evitar o seguinte código abaixo:
```js
let number = 10

number = number + 1;
```
- Também temos os operadores para fazer operações aritméticas com grandes valores, para isso usamos da seguinte maneira:
```js
// Incrementar mais de um
number += 10 // Soma +10 ao number


// Decrementar mais de um
number -= 5 // Tirando 5 do number
```
