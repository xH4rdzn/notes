___
- Para visualizar o conteúdo do *document*, podemos fazer da seguinte maneira:
```js
console.log(document)
```
- Agora no console do navegador irá aparecer toda a estrutura do documento **HTML**;
- Para obter o `title`da página:
```js
console.log(document.title)
```
- Para acessar um elemento pelo `id`, fazemos da seguinte maneira:
```js
const guest = document.getElementById("guest-2)
```
- **Nota-se que passamos o `id`do elemento como argumento para o `getElementById`;**
- Conseguimos também visualizar as propriedades do objetos que selecionamos, como no exemplo abaixo:
```js
console.dir(guest)
```
- Podemos acessar elementos através de sua classe
```js
const guestsByClass = document.getElementsByClassName("guest")
```
- **Passamos como argumento para o `getElementsByClassName` o nome da classe que queremos selecionar;
- Se quisermos pegar apenas o primeiro elemento através da classe, podemos fazer da seguinte maneira:
```js
console.log(guestsByClass.item(0))
```
- Ou da seguinte maneira:
```js
console.log(guestsByClassName[1])
```
- Podemos selecionar vários elementos pela *tag*
```js
const guestsByTag = document.getElementsByTagName("li")
```
- **Nota-se que passamos como argumento para o `getElementsByTagName`o elemento que queremos selecionar pela tag;
