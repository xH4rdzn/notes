___
- São conhecidas também como função de seta, podemos também como a [[Função anônima]], guardar ela em variáveis
- Como desmonstrado no exemplo abaixo:
```js
const showMessage = () => {
	console.log("Olá")
}
```
- E chamamos ela da mesma maneira como as outras funções:
```js
showMessage()
```
- Também podemos passar parâmetros
```js
const showMessage = (name) => {
	console.log("Olá, " + name)
}

showMessage('Igor')
```