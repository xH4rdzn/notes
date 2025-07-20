___
- Podemos aplicar herança entre classes, com a keyword `extends`, como no exemplo abaixo:
```js
class Animal {
	constructor(name) {
		this.name = name
	}

	makeNoise() {
		console.log("Som")
	}
}

// Classe que vai herdar

class Dog extends Animal {}
```
- Desta maneira, mesmo que a `class Dog`não tenha nada, ela vai herdar todas as propriedades e métodos da classe na qual ela herda, neste exemplo a `class Animal`;
