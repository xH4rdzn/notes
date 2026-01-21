___
- Como estamos salvando todos os nossos registros em memória, toda vez que a aplicação reinicia, perdemos os dados salvos.
- Mas podemos salvar as informações em arquivos físicos, para isso, na pasta `src`, vamos criar o arquivo `database.js`. e dentro dele vamos fazer o seguinte:
```js
export class Database {
	#database = {}
	
	select(table) {
		const data = this.#database[table] ?? []
		
		return data
	}
	
	insert(table, data) {
		if (Array.isArray(this.#database[table])) {
			this.#database[table].push(data)
		} else {
			this.#database[table] = [data]
		}
		
		return data
	}
}
```
- Agora para inserir o nosso banco de dados em nossa aplicação voltamos ao arquivo `server.js`e o adicionamos da seguinte maneira:
```js
const database = new Database()
```
- Agora no método ***POST***, trocamos onde adicionamos os dados para:
```js
const user = {
	id: 1,
	name,
	email,
}

database.insert('users', user)
```
- E no nosso método de ***GET***, fazemos da seguinte maneira:
```js
const users = database.select('users')

return res.end(JSON.stringify(users))
```