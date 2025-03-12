___
- Para identificar a moeda, precisamos fazer uma função, para fazer isso vamos seguir o exemplo:
```js
function convertCurrency(amount, price, symbol) {}
```
- Porém para recuperar esse valor, dependemos do `form`, então para identificar qual moeda e o valor, vamos usar um `switch`, ficando como no exemplo abaixo:
```js
form.onsubmit = (event) => {
	event.preventDefault()
	
	switch (currency.value) {
		case "USD":
			convertCurrency(amount.value, USD, "US$")
			break
		case "EUR":
			convertCurrency(amount.value, EUR, "€")
			break
		case "GBP":
			convertCurrency(amount.value, GBP, "£")
			break
	}
}
```
- Desta maneira ao selecionarmos a moeda no segundo `input`e digitar o valor já vamos ter acesso ao *valor, cotação e o simbolo* da moeda escolhida;