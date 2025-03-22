___
- o `setInterval()`, é muito parecido com o [[Conhecendo o setTimeout()|`setTimeout`]], a única diferença é que o `setInterval()`,ele fica executando a função a cada tempo que foi determinado na função
```js
let value = 10

setInterval(() => {
	console.log(value)
	value--
}, 1000)
```
- Porém se deixarmos como no exemplo acima, ele vai continuar infinitamente;
- Para poder parar usamos o método `clearInterval()`, então alteramos o código para:
```js
const interval = setInterval(() => {
	console.log(value)
	value--

	if (value === 0) {
		console.log("Feliz ano novo!")
		clearInterval(interval)
	}
}, 1000)
```
- Agora quando `value`chegar em 0, ele irá parar de executar o `setInterval()`;
