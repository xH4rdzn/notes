___
- Podemos criar um array usando [[Criando um array com um construtor|um construtor]];
- Mas também podemos criar da seguinte maneira:
```js
let fruits = ["Apple", "Banana", "Orange"]
```
- Para poder acessar alguma posição do array podemos fazer da seguinte maneira:
```js
// Acessa o item pelo índice
console.log(fruits[1])
```
- Podemos ver o tamanho do *array*, usando a propriedade `length`
```js
// Quantidade de itens no Array
console.log(fruits.length)
```
- Se colocarmos um índice que não tem no array ele retorna `undefined`;
- Para obtermos dinamicamente o último item do array podemos fazer da seguinte maneira:
```js
console.log(fruits[fruits.length - 1])
```
