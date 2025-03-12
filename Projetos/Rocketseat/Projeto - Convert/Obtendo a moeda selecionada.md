___
- Para selecionar a moeda, temos outro `input`, então precisamos selecionar esse outro `input`, para isso usar o `getElementById`
```js
const currency = document.getElementById('currency')
```
- Agora para pegar o valor desse elemento, podemos fazer isso ao ocorrer o evento de `submit`, mas para isso precisamos selecionar o `form`
```js
const form = document.querySelector('form')
```
- Agora podemos adicionar o `onsubmit`para observar os eventos
```js
form.onsubmit = (event) => {
	event.preventDefault()

	console.log(currency.value)
}
```
- Desta maneira ao enviar o `form`, irá gerar um *log* no console, com o valor da moeda escolhido;
