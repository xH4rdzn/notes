___
- Como vimos anteriormente podemos observar [[Eventos em um elemento específico]] com o javascript, mas agora vamos focar em eventos do formulário.
- Para isso devemos selecionar o formulário
```js
const form = document.querySelector("form")
```
- E depois disso usamos o método `addEventListener`, para poder observar os eventos que vão ocorrer nesse formulário
```js
form.addEventListener()
```
- Mas também existe outra maneira, neste caso podemos passar diretamente o evento que queremos observar, como no exemplo a seguir:
```js
form.onsubmit = (event) => {
	event.preventDefault()
	console.log("Você fez submit no form")
}
```
- Quando usamos da maneira acima, ele só vai funcionar o *último* que criamos;
- Quando usamos o `addEventListener`, ele executa todos;
