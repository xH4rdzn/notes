___
- Para podermos configurar um ambiente isolado para os testes, na raiz do nosso projeto vamos criar um arquivo com o nome de `.env.test`, nele vamos por as configurações voltados para o ambiente de teste. Esse arquivo entra no `.gitignore`
```.env
NODE_ENV=test
DATABASE_URL="./db/test.db"
```
- Agora no arquivo `index.ts`, que está dentro da pasta `src`, devemos fazer a alteração para a seguinte:
```ts
import { config } from 'dotenv'

if(process.env.NODE_ENV === 'test') {
	config({ path: '.env.test'})
} else {
	config()
}

// resto do código.
```
- Agora voltamos ao arquivo de teste e adicionamos a linha:
```ts
import { execSync } from 'node:child_process'

beforeEach(() => {
	execSync('npm run knex migrate:rollback --all')
	execSync('npm run knex migrate:latest')
})
```
- Desta maneira conseguimos ter um banco de dados limpo a cada teste.
 
