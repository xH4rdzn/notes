___
- Podemos converter uma string em um *array*, para isso usamos o método `split`, como no exemplo abaixo:
```js
let fullName = "Igor Rodrigues Coelho"

// Vai separar pelos espaços
console.log(fullName.split(" "))
```
- Podemos também criar um *array* de uma string separado por letras, para isso fazemos como no exemplo abaixo:
```js
console.log(Array.from(fullName))
```