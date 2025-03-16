___
- Como [[Como aplicar herança com classes ?|herdamos de outras classes]], podemos sobrescrever os métodos que vem da classe na qual ela herda, para fazermos isso podemos seguir o exemplo:
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

class Dog extends Animal {
	// Sobrescrevendo o método
	makeNoise() {
		console.log("Au..Au")
	}
}

class Cat extends Animal {
	// Sobrescrevendo o método
	makeNoise() {
		console.log("Miau..Miau")
	}
}
```
- Nota-se que para sobrescrever o método herdado, basta fazer a mesma estrutura na definição do método da classe pai;