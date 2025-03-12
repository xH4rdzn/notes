___
- Através do javascript, podemos criar elementos e inserir eles no [[DOM - Document Object Model|DOM]];
- Primeiro selecionamos o elemento no qual vamos querer adicionar um novo elemento:
```js
const guests = document.querySelector("ul")
```
- Agora precisamos criar o elemento que queremos adicionar onde adicionamos:
```js
const newGuest = document.createElement("li")
```
- Como na estrutura do exemplo tem um `span`dentro do elemento `li`precisamos criar ele também, fazendo como no exemplo acima:
```js
const guestName = document.createElement("span")
```
- E agora adicionamos um conteúdo ao `guestName`;
```js
guestName.textContent = "Igor"
```
- E agora precisamos adicionar o `guestName`no `newGuest`, usando o método `append`
```js
newGuest.append(guestName)
```
- Se quisermos adicionar antes de um outro filho usamos o método `prepend`;
- Podemos adicionar dois elementos de uma vez usando o método `append`, fazendo como no exemplo abaixo:
```js
newGuest.append(guestName, guestSurName)
```
- Outra maneira de adicionar elementos em outros elementos é usando o método `appendChild`, mas nesse método só podemos adicionar um novo elemento por vez:
```js
newGuest.appendChild(guestName)
```
- E agora só precisamos adicionar na *lista*, para fazermos isso, seguimos o exemplo:
```js
guests.append(newGuest)
```
- Agora só precisamos adicionar a estilização, para ficar igual aos outros elementos, para isso fazemos como no exemplo:
```js
newGuest.classList.add("guest")
```
