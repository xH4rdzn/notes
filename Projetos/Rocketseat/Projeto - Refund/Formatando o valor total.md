___
- Agora que exibimos o [[Calculando o valor total|total]], precisamos formatar ele, porém conseguimos reaproveitar a função `currencyBRL`, que criamos anteriormente, mas precisamos dar uma alterada, deixando como no exemplo abaixo:
```js
function updateTotals() {
	try {
		// Recupera todos os itens da lista
		const items = expenseList.children

		expenseQuantity.textContent = `${itens.length} ${items.length > 1 ? "despesas" : "despesa"}`

		let total = 0

		for(let item = 0; item < items.length; item++) {
			const itemAmount = items[item].querySelector(".expense-amount")

			let value = itemAmount.textContent.replace(/[^\d,]/g, "").replace("," , ".")
			// Converter o valor para float
			value = parseFloat(value)

			// Verificar se é um número valido
			if(isNaN(value)) {
				return alert("Não foi possível calcular o total. O valor não parace ser um número")
			}

			// Incrementar total
			total += Number(value)

		}
		
		const symbolBRL = document.createElement("small")
		symbolBRL.textContent = "R$"

		total = formartCurrencyBRL(total).toUpperCase().replace("R$", "")

		expensesTotal.innerHTML = ""

		expensesTotal.append(symbolBRL, total)

	} catch (error){
		alert("Não foi possível atualizar os totais")
		console.log(error)
	}
}
```