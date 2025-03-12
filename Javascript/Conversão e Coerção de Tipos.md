___
### Conversão de tipos
- `Type Casting`ou `Type Conversion`, ocorre quando você **explicitamente** transforma um valor de um tipo para outro. Isso é feito de forma consciente, usando funções ou métodos específicos para realizar a conversão.
- Como no exemplo abaixo:
```js
console.log(typeof "9") // Retorna string
console.log(typeof Number("9")) // Retorna Number
```

### Coerção de tipos
- Acontece de forma automática (implicitamente). O javascript tenta automaticamente converter um dos valores para um tipo compatível antes de realizar a operação
- Um exemplo de coerção
```js
console.log(typeof ("10" + 5))
```