___
- Agora que criamos o nosso [[Criando a li|item]], podemos criar o elemento da imagem, que mostra para o usuário qual foi a categoria da despesa
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
		
	} catch(error) {
		alert("Não foi possível atualizar a lista de despesas")
		console.log(error)
	}
}
```
- Agora para podermos testar, vamos selecionar a nossa lista, para podermos testar como ficou o ícone
```js
const expenseList = document.querySelector("ul")
```
- Voltamos a função `expenseAdd`e fazemos da seguinte maneira:
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

		// Adiciona as informações no item
		expenseItem.append(expenseIcon)

		// Adiciona o item na lista.
		expenseList.append(expenseItem)
		
	} catch(error) {
		alert("Não foi possível atualizar a lista de despesas")
		console.log(error)
	}
}
```