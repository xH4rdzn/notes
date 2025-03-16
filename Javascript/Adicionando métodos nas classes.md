___
- Métodos são funções que podemos acessar dentro da classe;
- Para adicionar métodos fazemos como no exemplo:
```js
class User {
	constructor(name, email) {
		this.name = name
		this.email = email
	}

	// Adicionando um método
	sendEmail() {
		console.log("Email Enviado")
	}
}
```
- Porém para acessar esse método, precisamos fazer uma instancia dessa classe:
```js
const user = new User("Igor", "igor@email.com")
```
- E usamos o método a partir da variável de referência para a classe que instanciamos:
```js
user.sendEmail()
```