___
- Vamos utilizar o prisma, para instalar ele vamos usar o comando:
```zsh
npm i prisma@6.2.1 -D
```
- E agora vamos instalar o `prisma/client
```zsh
npm i @prisma/client@5.2.1
```
- Agora vamos executar o prisma, com o comando:
```zsh
npx prisma init --datasource-provider sqlite
```
- Agora irá ser criado a pasta `prisma`;
- Agora dentro da pasta `src`, vamos criar a pasta `database`, e dentro dessa pasta vamos criar o arquivo `prisma.ts`, e dentro desse arquivo vamos fazer o seguinte:
```ts
import { PrismaClient } from "@prisma/client"

export const prisma = new PrismaClient({
	log:["query"],
})
```
- Desta maneira já temos o prisma instalado e configurado;
