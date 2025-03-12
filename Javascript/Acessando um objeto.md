___
- Para acessar as propriedades e métodos de um objeto, podemos usar a notação de ponto:
```js
console.log(user.email)
```
- Se quisermos acessar uma propriedade especifica de um objeto aninhado, fazemos da seguinte maneira:
```js
console.log(user.name.first_name)
```
- Para acessar uma função, podemos fazer da seguinte maneira:
```js
user.message()
```
- Além da notação ponto, podemos usar a notação de colchetes
```js
console.log(user["email"])
```
- Para objetos aninhados:
```js
console.log(user["name"]["first_name"])
```
- Para acessar funções:
```js
user["message"]()
```