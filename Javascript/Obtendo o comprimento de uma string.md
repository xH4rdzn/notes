___
- Podemos obter o tamanho de uma string usando a propriedade `length`, como no exemplo abaixo:
```js
let message = "Estou estudando os fundamentos do javascript"

console.log(message.length) // Retorna o comprindo da string
```
- **Essa propriedade conta com os *espaços*;
- Podemos também verificar quantos dígitos tem um número, para fazer isso podemos fazer como no exemplo abaixo:
```js
let value = 12324

console.log(String(value).length)

// Ou então podemos fazer assim

console.log(value.toString().length)
```