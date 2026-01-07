___
### Stateful vs. Stateless
- Uma aplicação *Stateful*, sempre vai ter alguma informação sendo guardada na memória, para seu funcionamento. A partir do momento em que essa aplicação é derrubada esses dados se perdem, fazendo alteração no funcionamento da aplicação.
- Uma aplicação *Stateless*, não guarda nada em memória, normalmente as informações são salvas em locais externos, como banco de dados. E mesmo quando a aplicação é reiniciada, o seu funcionamento e informações se mantém os mesmos.

- Em nossa aplicação, vamos salvar tudo em memória por enquanto, então para isso, vamos criar um array, que vai armazenar os dados que serão salvos em memória.
```js
const users = []
```
- Agora em nossa rota de ***`POST`*** de *`users`* vamos adicionar um objeto no array:
```js
if (method === 'POST' && url === '/users') {
	users.push({
		id: 1,
		name: 'John Doe',
		email: 'johndoe@email.com',
	})
	
	return res.end('Criação de usuário')
}
```
- E na rota de ***`GET`***, vamos ter que transformar esse array em uma estrutura de dados conhecida como ***JSON***, que significa ***Javascript Object Notation***. Com essa estrutura de dados conseguimos transitar dados entre várias aplicações.
```js
if (method === 'GET' && url === '/users') {
	return res.end(JSON.stringify(users))
}
```
- Porém para podermos identificar tanto no back-end, como no front-end, precisamos usar os ***Headers***, que são os cabeçalhos que são metadados, que são informações adicionais, que mostram como os dados devem ser interpretados.
- Para podermos setar um *header*, devemos fazer o seguinte:
```js
if (method === 'GET' && url === '/users') {
	return res
	.setHeader('Content-type', 'application/json')
	.end(JSON.stringify(users))
}
```
- Esses *headers*, conseguimos recuperar tanto da requisição, como enviar eles em uma resposta.