___
- Podemos recuperar o valor do `input`, para isso precisamos primeiro selecionar o input
```js
const input = document.querySelector("input")
```
- Depois adicionamos o `addEventListener`
```js
input.addEventListener("input", () => {
	const value = input.value
	
	const regex = /\D+/g

	// Retorna o padrão encontrado na string
	// console.log(value.match(regex))

	// Testa o valor e se atende o padrão(retorna true ou false)
	const isValid = regex.test(value)
})
```
