___
### Objeto
- Uma coleção de dados e/ou funcionalidades;
- Podem ter propriedades e métodos;

- Para criarmos um objeto vazio, podemos fazer da seguinte maneira:
```js
const objetoVazio = {}
```
- Para criar um objeto com propriedades e métodos, podemos seguir o exemplo:
```js
const user = {
	email: "igor@email.com",
	age: 26,
}
```
- Dentro do objeto usamos o `:` para dar valor para uma propriedade;
- É comum chamarmos de chave-valor;
- Podemos ter propriedades aninhadas, como no exemplo a baixo:
```js
const user = {
	email: "igor@email.com",
	age: 26,
	name: {
		firstName: "Igor",
		surname: "Coelho",
	},
}
```
- É comum usarmos propriedades aninhadas para propriedades compostas, como por exemplo o endereço, que podemos ter nome da rua, número da casa, estado, etc.
- Também podemos criar funções dentro dos objetos, podemos chamar de métodos também
```js
const method = {
	message: () => {
		console.log("Isso é um método")
	}
}
```