___
- Agora, para escrever o nosso banco de dados em arquivos físicos, podemos fazer da seguinte maneira:
```js
import fs from 'node:fs/promises'

const databasePath = new URL('../db.json', import.meta.url)

export class Database {
	#database = {}
	
	// Ler o arquivo criado, e se o arquivo não existir chama o método persist() e cria o arquivo.
	constructor() {
		fs.readFile(databasePath, 'utf-8').then(data => {
			this.#database = JSON.parse(data)
		})
		.catch(() => {
			this.#persist()
		})
	}
	
	// Método que vai escrever o nosso arquivo físico
	#persist() {
			fs.writeFile(databasePath, JSON.stringify(this.#database))
	}
	
	
	select(table) {
		const data = this.#database[table] ?? []
		
		return data
	}
	
	insert(table, data) {
		if(Array.isArray(this.#database[table])) {
			this.#database[table].push[data]
		} else {
			this.#database[table] = [data]
		}
		
		this.#persist()
		
		return data
	}
	
}
```
- Desta maneira ao reiniciar a nossa aplicação os dados continuarão salvos, no arquivo `db.json`.