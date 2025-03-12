___
- Inicialmente podemos criar um *array* vazio e ir adicionando os itens;
- Para adicionar usamos o método `push`, como no exemplo abaixo:
```js
let users = []

users.push("Igor")
users.push("Lucas")
users.push("Caio")
```
- Método `push`adiciona no final da lista
- Já o método `unshift`, adiciona um item no inicio do *array*;
```js
users.unshift("Ana")
```
- Para remover um item do array usamos o método `shift`, esse método remove do inicio do array
```js
users.shift()
```
- Se quisermos remover do final usamos o método `pop`;
```js
users.pop()
```