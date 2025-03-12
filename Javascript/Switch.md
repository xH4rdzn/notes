___
- É uma estrutura bem interessante quando queremos analisar caso a caso;
- Funciona como no exemplo abaixo:
```js
let option = 1

switch (option) {
	case 1:
		console.log("Consultar pedido")
		break
	case 2:
		console.log("Falar com atendente")
		break
}
```
- Se não usarmos o `break`, ele vai executar todos os casos abaixo do caso que foi selecionado;
- Para tratar todos os casos, podemos usar o `default`, para caso não seja escolhido nenhuma das condições definidas, ele vai ser executado;
```js
let option = 1

switch(option) {
	case 1:
		console.log('Consultar pedido')
		break
	case 2:
		console.log('Falar com atendente')
		break
	default:
		console.log('Opção Inválida')
}
```