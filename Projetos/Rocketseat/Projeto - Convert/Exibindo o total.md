___
- Precisamos selecionar o elemento que irá mostrar o valor total, para isso usamos:
```js
const result = document.getElementById('result')
```
- Para calcular o valor total, vamos utilizar a função `convertCurrency`, para isso vamos continuar nela:
```js
function convertCurrency(amount, price, symbol) {
	try {
		description.textContent = `${symbol} 1 = ${formatCurrencyBRL(price)}`

		let total = amount * price
		result.textContent = total

		footer.classList.add('show-result')
	} catch (error) {
		footer.classList.remove('show-result')
		console.log(error)
		alert("Não foi possível converter. Tente novamente mais tarde.")
	}
}
```