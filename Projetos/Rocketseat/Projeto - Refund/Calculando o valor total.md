___
- Agora que já pegamos o item do valor, precisamos transformar ele em número novamente, para fazer isso continuamos da seguinte maneira:
```js
function updateTotals() {
	try {
		// Recupera todos os itens da lista
		const items = expenseList.children

		expenseQuantity.textContent = `${itens.length} ${items.length > 1 ? "despesas" : "despesa"}`

		let total = 0

		for(let item = 0; item < items.length; item++) {
			const itemAmount = items[item].querySelector(".expense-amount")

			let value = itemAmount.textContent.replace(/[^\d]/g, "").replace("," , ".")
			// Converter o valor para float
			value = parseFloat(value)

			// Verificar se é um número valido
			if(isNaN(value)) {
				return alert("Não foi possível calcular o total. O valor não parace ser um número")
			}

			// Incrementar total
			total += Number(value)

		}

	} catch (error){
		alert("Não foi possível atualizar os totais")
		console.log(error)
	}
}
```
- Agora precisamos selecionar o valor total para poder atualizar de acordo com os items que adicionamos, para isso precisamos selecionar o total, para isso vamos usar:
```js
const expensesTotal = document.querySelector("aside header h2")
```
- Agora voltamos onde estamos calculando o total e fazemos o seguinte: 
```js
function updateTotals() {
	try {
		// Recupera todos os itens da lista
		const items = expenseList.children

		expenseQuantity.textContent = `${itens.length} ${items.length > 1 ? "despesas" : "despesa"}`

		let total = 0

		for(let item = 0; item < items.length; item++) {
			const itemAmount = items[item].querySelector(".expense-amount")

			let value = itemAmount.textContent.replace(/[^\d]/g, "").replace("," , ".")
			// Converter o valor para float
			value = parseFloat(value)

			// Verificar se é um número valido
			if(isNaN(value)) {
				return alert("Não foi possível calcular o total. O valor não parace ser um número")
			}

			// Incrementar total
			total += Number(value)

		}

		expensesTotal.textContent = total

	} catch (error){
		alert("Não foi possível atualizar os totais")
		console.log(error)
	}
}
```
- Agora só precisamos [[Formatando o valor total|formatar o valor total]]
- 