___
- Callback function, é uma função passada para outra função como um argumento.
- Como no exemplo abaixo:
```js
function execute(taskName, callback) {
	console.log("Executando a tarefa: ", taskName)
	callback()
}

function callback() {
	console.log("Tarefa finalizada")
}

execute("Download do arquivo", callback)
```
- Uma outra maneira é criando a função no próprio parâmetro:
```js
execute("Upload do arquivo", function () {
	console.log("Função de callback com uma função anônima.")
})
```
- Também é possível criar usando a [[Arrow Function]];
```js
execute("Excluindo arquivo...", () => {
	console.log("Arquivo Excluído!")
})
```
- Podemos também fazer isso com um *shorthand*, com a [[Arrow Function]], como no exemplo abaixo:
```js
execute("Salvando arquivo...", () => console.log("Arquivo Savlo!"))
```
