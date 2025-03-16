___
- Como tudo no javascript é um objeto, podemos personalizar mensagens de erro, ao ser lançados exceções, como no exemplo abaixo:
```js
let obj = []

try {
	obj.execute()
} catch(error) {
	if(error instanceof TypeError) {
		console.log("Método indisponível")
	}
}
```
- Usamos a keyword `instanceof`, para verificar e personalizar uma mensagem de acordo com o tipo de erro;