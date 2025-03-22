___
- Conseguimos *congelar* os objetos, para impedir alterações nele;
- Para fazer isso seguimos o exemplo:
```js
const book = {
	title: "Objetos Imutáveis",
	category: "javascript",
	author: {
		name: "Rodrigo",
		email: "rodrigo@email.com"
	},
}

// Alterando a category do book
book.category = "HTML"
```
- O javascript em si não impõe restrições à modificação dos objetos;
- Para **congelar** os objetos, podemos usar o método `Object.freeze()`;
```js
const book = {
	title: "Objetos Imutáveis",
	category: "javascript",
	author: {
		name: "Rodrigo",
		email: "rodrigo@email.com"
	},
}

// Congelando o objeto
Object.freeze(book)
```
- Porém esse método não faz o *congelamento* dos objetos aninhados;
- Chamamos isso de `Shallow Freezing`, pois ele não impede alterações profundas (objetos aninhados) dos objetos;
