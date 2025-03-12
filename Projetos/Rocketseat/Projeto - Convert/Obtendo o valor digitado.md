___
- Para poder recuperarmos o valor digitado no `input`, precisamos selecionar ele primeiro, para isso vamos fazer da seguinte maneira:
```js
const amount = document.querySelector('#amount')
```
- Após selecionar o `input`, precisamos adicionar o `addEventListener`, para observar os eventos que vão ocorrer nesse elemento
```js
amount.addEventListener("input", () => {
	console.log(amount.value)
})
```
- Desta maneira já estamos recuperando o valor que está no `input`;
