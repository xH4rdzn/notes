___
- Como vimos anteriormente, conseguimos usar a reposta de uma *Promise*, usando o [[Conhecendo promises|then, catch e finally]], mas também podemos, usar uma outra anotação que é a `async` e `await`, como demostrado no exemplo abaixo:
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

async function fetch() {
	const response = async asyncFunction()
	console.log(response)
}

fetch()
```
- Só conseguimos usar o `await`em uma função que seja assíncrona, desta maneira ele aguarda a resposta da *Promise*, para continuar a execução do programa.
- Podemos também usar `async-await`em [[Arrow Function]];
```js
const fetch = async () => {
	const response = await asyncFunction()
	console.log(response)
}
```
- Usando o `async-await`, também podemos usar o `then, catch e finally`, a única diferença é que no lugar de `then`, usamos o `try`;
- Ficando como no exemplo abaixo:
```js
const fetch = async () => {
	try {
		const response = await asyncFunction()
		console.log(response)
	} catch(error) {
		console.log(error)
	} finally {
		console.log("Fim da execução")
	}
}
```