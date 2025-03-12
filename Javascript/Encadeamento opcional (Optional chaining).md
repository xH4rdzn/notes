___
- O encadeamento opcional. Se a propriedade ou método chamado é `nullish`(null ou undefined), a expressão retorna `undefined`em vez de gerar um erro.
- Útil ao explorar o conteúdo de um objeto quando não existe garantia da existência de determinadas propriedades obrigatórias.
```js
const user = {
	name: "Igor",
	adress: {
		street: "Rua Javascript",
		number: 256,
	},
}

console.log(user?.adress?.street)
```
- Agora podemos fazer isso para métodos também, para métodos fazemos como no exemplo abaixo:
```js
user.message?.()
```
- Caso tenha o método implementado, ele irá executar, caso não tenha não irá dar erro, mas não irá acontecer nada;