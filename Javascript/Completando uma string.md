___
- Podemos completar as strings, com os métodos `padStart`e `padEnd`;
- O método `padStart`, preenche a string do início.
```js
const maskedNumber = lastDigits.padStart(creditCard.length, "X")

// Resultado
// XXXXXXXXXXXXX4928
```
- Já o método `padEnd`, preenche a string no final;
```JS
const number = "123"
console.log(number.padEnd(10, "#"))

// Resultado
// 123#######
```
