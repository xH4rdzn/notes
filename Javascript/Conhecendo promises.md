___
- Criando uma função que retorna uma *Promise*
```js
// Função que retorna uma Promise
function asyncFunction() {
	return new Promise((resolve, reject) => {
		// Simula uma operação assíncrona.
		setTimeout(() => {
		
			const isSuccess = true

			if(isSUccess) {
				resolve("A operação foi concluída com sucesso!")
			} else {
				reject("Algo deu errado")
			}
		}, 3000)
	})
}
```
- Visualizando o retorno de uma *Promise*, para isso javascript disponibiliza alguns métodos que são: **then, catch** e o **finally**
- Usamos o *then*, quando a *Promise*, foi resolvida e queremos a reposta.
- Usamos o *catch*, para tratar o erro quando a *Promise* é rejeitada.
- Usamos o *finally*, esse bloco executa mesmo quando a *Promise* é rejeitada;
```js
asyncFunction().then((response) => {
	console.log("Sucesso", response)
}).catch((error) => {
	console.log(error)
}).finally(() => {
	console.log('Fim da execução')
})
```