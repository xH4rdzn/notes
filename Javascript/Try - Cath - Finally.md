___
- Para usarmos o [[Javascript/Tratamento de Exceções]], com o bloco `Try-Cath`, fazemos da seguinte maneira:
```js
try {
	console.log(result)
} catch(error) {
	console.log(error)
}
```
- Nota-se que conseguimos capturar o `error`no `catch`e devolvermos uma reposta mais amigável;
- Ainda temos um terceiro bloco que chamamos de `finally`, esse bloco executa algo independente se deu certo ou se deu erro;
- Nós conseguimos lançar exceções, como no exemplo abaixo:
```js
let result = 1

try {
	if (result === 0) {
		throw new Error('0 valor é igual a 0')
	}
} catch (error) {
	console.log(error)
} finally {
	console.log('Fim')
}
```