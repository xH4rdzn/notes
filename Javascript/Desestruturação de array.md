___
- `Destructuring assignment`(desestruturação) permite extrair dados de arrays ou objetos em variáveis distintas.
```js
const data = ["Igor Coelho", "igor@email.com"]

// Desestruturando array
const [username, email] = data

// Usando as variáveis
console.log("Nome:", username)
console.log("Email:", email)
```
- Outro exemplo:
```js
const fruits = ["Banana", "Apple", "Orange"]

// Desestruturar somente o primeiro
const [banana] = fruits
console.log(banana)

// Desestruturar a segunda posição
const [_,apple] = fruits

// Desestruturando a terceira posição
const [, , orange] = fruits
```
- Podemos usar a `,` para ignorar as posições;
