___
- Agora vamos criar uma função para atualizar a quantidade de despesas e o valor total
```js
function updateTotals() {
	try {
		// Recupera todos os itens da lista
		const items = expenseList.children
	} catch (error){
		alert("Não foi possível atualizar os totais")
		console.log(error)
	}
}
```
- Agora voltamos a função `expenseAdd`e no final dela adicionamos essa função:
```js
// código acima
updateTotals()
```
- Agora precisamos verificar onde está o número que queremos atualizar e selecionar esse elemento
```js
const expenseQuantity = document.querySelector("aside header p span")
```
- Agora podemos atualizar a quantidade da seguinte maneira:
```js
function updateTotals() {
	try {
		// Recupera todos os itens da lista
		const items = expenseList.children

		expenseQuantity.textContent = `${itens.length} ${items.length > 1 ? "despesas" : "despesa"}`
	} catch (error){
		alert("Não foi possível atualizar os totais")
		console.log(error)
	}
}
```
- Desta maneira também conseguimos deixar o texto dinâmico de acordo com a quantidade de items que temos na lista.