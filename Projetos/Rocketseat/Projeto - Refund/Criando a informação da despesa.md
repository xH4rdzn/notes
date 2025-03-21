___
- Agora vamos continuar adicionando as informações, depois da parte que adicionamos o [[Criando o ícone da categoria|ícone]], vamos continuar:
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
		

		// Adiciona as informações no item
		expenseItem.append(expenseIcon, expenseInfo)

		// Adiciona o item na lista.
		expenseList.append(expenseItem)
		
	} catch(error) {
		alert("Não foi possível atualizar a lista de despesas")
		console.log(error)
	}
}
```