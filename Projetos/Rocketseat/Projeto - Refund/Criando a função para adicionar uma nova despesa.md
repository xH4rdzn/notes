___
- Agora que já criamos [[Criando um objeto de nova despesa|um objeto para a nova despesa]], precisamos criar uma função para adicionar essa nova despesa em uma lista, e essa função vai ficar responsável também por montar o item que vamos por nessa lista, para isso fazemos como no exemplo:
```js
// Criando a função da adicionar uma nova despesa
function expenseAdd(newExpense) {
	try {
		
	} catch(error) {
		alert("Não foi possível atualizar a lista de despesas")
		console.log(error)
	}
}
```
- Agora colocamos essa função no evento do formulário, para ao enviar esse item ser adicionado na lista
```js
form.onsubmit = (event) => {
	event.preventDefault()

	const newExpense = {
		id: new Date().getTime(),
		expense: expense.value,
		category_id: category.value,
		category_name: category.options[category.selectedIndex].text,
		amount: amount.value,
		created_at: new Date(),
	}

	expenseAdd(newExpense)
}
```
