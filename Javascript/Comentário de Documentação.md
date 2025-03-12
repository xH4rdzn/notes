___
- Comentário de documentação em JavaScript (sintaxe de JSDoc).
- O JSDoc é uma padrão para incorporar documentação no código-fonte a partir desses comentários.
- Usamos eles como no exemplo abaixo:
```js
/**
	* @param {String} email user email.
	* @param {String} password more than 6 characters.
	* @returns {Number} user id.
*/
function signIn(email, password) {
	// Todo o fluxo de autenticação do usuaŕio
}
```