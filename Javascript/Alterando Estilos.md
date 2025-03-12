___
- Através do javascript, podemos alterar os estilos dos elementos, como adicionar uma classe ou remover;
- No exemplo abaixo vamos adicionar uma classe dinamicamente em um input pelo javascript
```js
const input = document.querySelector("#name")
input.classList.add("input-error")
```
- O método `classList`, é onde podemos adicionar ou remover uma `class`ao elemento;
- Como vamos adicionar usamos o `add` e ele recebe como argumento o nome da classe que vamos adicionar ao elemento;
- Se quisermos remover a classe, usamos o `remove`, como no exemplo abaixo:
```js
input.classList.remove("input-error")
```
- Temos também o `toggle`, esse método faz com que, se a `class`não existe ele adiciona, se existir ele remove;
```js
input.classList.toggle("input-error")
```
- Podemos também alterar estilos pelo javascript, como no exemplo abaixo que vamos mudar a cor de um botão:
```js
const button = document.querySelector("button")
button.style.backgroundColor = "red"
```