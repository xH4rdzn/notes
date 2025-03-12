___
- Para formatar a para real, vamos criar uma função
```js
function formatCurrencyBRL(value) {
	return Number(value).toLocaleString("pt-BR", {
		style: "currency",
		currency: "BRL",
	})
}
```
- Agora voltamos ao `description`e em vez de passarmos o `price`, passamos a função
```js
description.textContent = `${symbol} 1 = ${formatCurrencyBRL(price)}`
```
- Desta maneira já irá formatar o valor da cotação atual, para o `BRL`;
