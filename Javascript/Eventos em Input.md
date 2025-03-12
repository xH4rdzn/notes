___
- Agora vamos falar de [[Eventos]], focados em **inputs**
- Primeiro vamos selecionar o *input*
```js
const input = document.querySelector("input")
```
- Evento de `keydown`, é quando uma tecla é pressionada, podendo ser qualquer tecla;
```js
input.addEventListener("keydown", (event) => {
	console.log(event.key) // assim só recuperamos a letra ou a tecla pressionada
})
```
- Evento de `keypress`, é quando uma tecla do tipo caractere é pressionada (letras, números, pontos, espaço e etc.);
```js
input.addEventListener("keypress", (event) => {
	console.log(event.key)
})
```
- O evento de `change`, é quando o conteúdo do *input*, muda, mas precisamos sair do input;
```js
input.onchange = (() => {
	console.log("O input mudou")
})
```