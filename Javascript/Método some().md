___
- O método `some()`, teste se ao menos um dos elementos no array passa na condição e retorna um valor true ou false.
```js
const ages = [15, 30, 39, 40]

const result = ages.some((age) => age < 18)
console.log(result)
```
- Esse método retorna `true`se pelo menos um item do array atender a condição;
- Retorna `false`, caso nenhum item do array atender a condição;