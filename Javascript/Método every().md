___
- O método `every()`, testa se todos os elementos do array passam na condição e retorna um valor *boolean*
```js
const ages = [15, 30, 39, 29]

// Verificando se todas as idades são maiores ou igual a 18
const result = ages.every((age) => age >= 18)
console.log(result) // Retorna false, pois um item não atende a condição
```