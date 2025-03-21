___
-  Para criarmos o valor da despesa, vamos continuar na nossa função de adicionar um novo item:
```js
function expenseAdd(newExpense) {
	try {
		// Criando o elemento (li)
		const expenseItem = document.createElement("li")
		expenseItem.classList.add("expense")

		// Cria o ícone da categoria
		const expenseIcon = document.createElement('img')
		expenseIcon.setAttribute("src", `img/${newExpense.category_id}.svg`)
		expenseIcon.setAttribute("alt", newExpense.category_name)

		// Cria a info da despesa
		const expenseInfo = document.createElement("div")
		expenseInfo.classList.add("expense-info")

		// Cria o nome da desepsa
		const expenseName = document.createElement("strong")
		expenseName.textContent = newExpense.expense

		// Cria a categoria da despesa
		const expenseCategory = document.createElement("span")
		expenseCategory.textContent = newExpense.category_name

		// Adicionando os itens na div
		expenseInfo.append(expenseName, expenseCategory)
		
		// Cria o valor da despesa
		const expenseAmount = document.createElement("span")
		expenseAmount.classList.add("expense-amount")
		expenseAmount.innerHTML = `<small></small>${newExpense.amount.toUpperCase().replace("R$", "")}`

		// Adiciona as informações no item
		expenseItem.append(expenseIcon, expenseInfo, expenseAmount)

		// Adiciona o item na lista.
		expenseList.append(expenseItem)
		
	} catch(error) {
		alert("Não foi possível atualizar a lista de despesas")
		console.log(error)
	}
}
```