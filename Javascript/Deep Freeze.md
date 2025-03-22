___
- Como vimos anteriormente conseguimos [[Shallow freezing|congelar o objeto]], para impedir alterações nos objetos, porém ele não impedia alterações em projetos aninhados;
- Para podermos fazer o *congelamento total*, ou seja também impedir alterações em objetos aninhados, fazemos como no exemplo abaixo:
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
function deepFreeze(object) {

	// Obtém um array com todas as propriedades do objeto	 
	const props = Reflect.ownKeys(object)

	// Itera sobre todas as propriedades do objeto
	for(const prop of props) {

		// Obtém o valor associado a propriedade atual
		const value = object[prop]

		// Verifica se o valor é um objeto ou função, para continuar aplicando o deep Freeze em objetos aninhados
		if(value && typeof value === "object" || typeof value === "function") {
			deepFreeze(value)
		}

	}

	return Object.freeze(object)
}

// Chamando a função para congelar o objeto com o Deep Freeze
deepFreeze(book)


```
- Agora desta maneira, não conseguimos alterar diretamente nenhuma propriedade do objeto, em nenhum nível;