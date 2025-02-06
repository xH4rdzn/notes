___
- Agora vamos criar a conexão com o banco de dados, voltamos ao código e dentro da pasta `database`, vamos criar o arquivo `knex.ts`.
- E dentro desse arquivo vamos por o seguinte código:
```Ts
import { knex as knexConfig } from "knex"

import config from "../../knexfile"

export const knex = knexConfig(config)
```
- Desta maneira já temos uma conexão com o banco de dados.