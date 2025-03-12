___
- Para exibir o resultado, vamos usar um `footer`, como o CSS já estava pronto, precisamos apenas adicionar uma classe, para que o `footer`apareça, para fazer isso vamos usar a função `convertCurrency`, deixando ela da seguinte maneira:
```js
function convertCurrency(amount, price, symbol) {
	try {
		footer.classList.add('show-result')
	} catch (error) {
		footer.classList.remove('show-result')
		console.log(error)
		alert("Não foi possível converter. Tente novamente mais tarde.")
	}
}
```
- Não podemos esquecer de selecionar o elemento `footer`, para isso usamos:
```js
const footer = document.querySelector('main footer')
```
- Usamos o bloco `try-catch`, para tentarmos executar algo e caso der erro fazer um tratamento desse erro e remover o `footer`da tela;
- Usamos o método `classList`, para adicionar ou remover classes de CSS através do javascript;
