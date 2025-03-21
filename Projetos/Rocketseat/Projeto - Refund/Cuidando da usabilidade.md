___
- Podemos limpar o formulário toda vez que adicionarmos uma nova despesa;
- Para isso vamos criar um novo método
```js
function formClear() {
	expense.value = ""
	category.value = ""
	amount.value = ""

	expense.focus()
}
```
- Agora chamamos esse `formClear`, toda vez que formos adicionar um novo item, então adicionamos essa função na função `expenseAdd`;