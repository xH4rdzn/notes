___
- Para podermos `tiparmos` o `Knex`, podemos fazer da seguinte maneira:
1. Na pasta `src`, criamos a pasta `@types`, ou apenas `types`, essa pasta vai ser usada para sobrescrever tipagens de outras bibliotecas
2. Dentro dessa pasta vamos criar o arquivo `knex.d.ts`
	- O arquivo `.d`, é de definição de tipos;
3. Agora fazemos como no exemplo abaixo:
```ts
import { Knex } from 'knex'

declare module 'knex/types/tables' {
	export interface Tables {
		transactions: {
			id: string
			title: string
			amount: number
			created_at: string
			session_id?: string
		}
	}
}
```
- Nesse arquivo definimos as tabelas que vamos ter na nossa aplicação e quais dados cada tabela possui, assim fica mais fácil de se lidar com o `Knex`;