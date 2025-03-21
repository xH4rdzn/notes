___
- Agora que fizemos a estrutura [[Criando a função para adicionar uma nova despesa|da função que vai adicionar uma nova despesa]], podemos começar a criar dentro do bloco `try`, o elemento que vai ser adicionado na lista:
```js
function expenseAdd(newExpense) {
	try {
		const expenseItem = document.createElement("li")
		expenseItem.classList.add("expense")	
	} catch(error) {
		alert("Não foi possível atualizar a lista de despesas")
		console.log(error)
	}
}
```
- Com o código acima, criamos o elemento da lista `li`, e adicionamos sua estilização;