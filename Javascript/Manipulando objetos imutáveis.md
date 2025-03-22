___
- Agora vamos aprender como manipular um objeto, usando o principio da imutabilidade, preservando o objeto original;
- Como no exemplo abaixo:
```js
const book = {
	title: "Objetos Imutáveis",
	category: "javascript",
	author: {
		name: "Rodrigo",
		email: "rodrigo@email.com"
	}
}

// Manipulando

const updatedBook = {
	...book,
	title: "Criando um front-end moderno com HTML",
	category: "html",
}
```
- No exemplo acima, vamos ter 2 objetos, o original, e o novo objeto;
- Nele podemos adicionar até novas propriedades sem alterar em nada o objeto original
- Podemos também retirar propriedades que não queremos, fazendo a desestruturação
```js
const book = {
	title: "Objetos Imutáveis",
	category: "javascript",
	author: {
		name: "Rodrigo",
		email: "rodrigo@email.com"
	}
}

// Desestruturando

const { category, ...bookWithoutCategory} = book
```
- No exemplo acima, retornamos o objeto sem a propriedade `category`, e podemos retirar qualquer propriedade do objeto;