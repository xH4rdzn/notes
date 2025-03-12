___
- Função anônima é uma função que não tem nome;
- São aquelas que guardamos dentro de variáveis, como no exemplo a seguir;
```js
const showMessage = function() {
	return 'Olá Igor'
}
```
- E chamamos essa função da mesma maneira que chamamos as outras:
```js
console.log(showMessage())
```
- Podemos passar parâmetros para as funções anônimas:
```js
const showMessage2 = function(name) {
	return "Olá " + name
}

console.log(showMessage2("Igor"))
```