___
- Agora vamos pegar as demais informações do formulário:
```js
const expense = document.getElementById('expense')
const category = document.getElementById('category')
const form = document.querySelector('form')
```
- Agora podemos criar o nosso evento de formulário:
```js
form.onsubmit = (event) => {
	event.preventDefault()
}
```
- Para que ele não fique recarregando a página toda vez que enviarmos o formulário;