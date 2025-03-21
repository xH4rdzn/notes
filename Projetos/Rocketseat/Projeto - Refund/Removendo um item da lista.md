___
- Agora precisamos escolher o item pai, se não vamos apagar apenas a imagem, para isso vamos usar:
```js
expenseList.addEventListener("click", function(event) {
	if(event.target.classList.contains("remove-icon")){
		const item = event.target.closest(".expense")
		item.remove()
	}

	updateTotals()
})
```
- Usamos a função `updateTotals`, para poder atualizar novamente os valores, após remover um item da lista;
