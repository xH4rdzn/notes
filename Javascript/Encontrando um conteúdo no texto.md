___
- Para obtermos a posição de uma certa palavra, podemos usar o método `indexOf`, como no exemplo abaixo:
```js
let message = "Estou estudando os fundamentos do Javascript"

console.log(message.indexOf("estudando"))
```
- Quando a palavra não é encontrada, ele retorna *-1*
- Podemos verificar se existe uma palavra dentro de uma string, para isso usamos o método `includes`;
- O `includes`, retorna um *boolean*;
```js
let message = "Estou estudando os fundamentops do Javascript"

console.log(message.includes("Javascript"))
```
