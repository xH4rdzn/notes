___
- Outra maneira de selecionar elementos é usando o `querySelector`;
- Como no exemplo abaixo:
```js
const guest = document.querySelector("")
```
- Passamos como argumentos para ele uma combinação que resulta na seleção dos elementos;
- Se quisermos selecionar pelo `id`, passamos da seguinte maneira:
```js
const guest = document.querySelector("#guest-1")
```
- Se quisermos selecionar pela `class`, passamos da seguinte maneira:
```js
const guest = document.querySelector(".guest")
```
- Porém ele sempre vai retornar apenas o primeiro, se quisermos pegar todos os elementos usamos o método `querySelectorAll`
```js
const guest = document.querySelectorAll(".guest")
```
