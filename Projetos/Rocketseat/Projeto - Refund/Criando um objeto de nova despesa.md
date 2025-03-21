___
- Ainda dentro do nosso evento de formulário, podemos criar um objeto para representar a despesa que irá ser enviada pelo formulário
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
}
```
- Desta maneira já temos todas as informações necessárias que são enviadas pelo formulário.