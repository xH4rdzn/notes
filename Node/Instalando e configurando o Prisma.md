___
- Para instalarmos o `Prisma`, usamos o comando abaixo:
```zsh
npm i prisma
```
- Agora precisamos iniciar o `Prisma`, para isso usamos o comando abaixo:
```zsh
npx prisma init --datasource-provider postgresql
```
- `--datasource-provider` -> passamos o banco de dados que vamos utilizar, no exemplo acima, vamos usar um banco de dados `postgresql`;
- Após isso será gerado uma pasta `prisma`, e um arquivo `.env`;
- O arquivo `.env`, são variáveis de ambiente.
- Dentro da pasta prisma, irá ser gerado um arquivo com o nome: `schema.prisma`, nesse arquivo vai conter as informações do nosso banco de dados, assim como configurações de conexão.
- No arquivo `.env`, precisamos modificar o `DATABASE_URL`, passando as informações que passamos na criação do nosso container [Docker](./Criando%20o%20Docker%20Compose.md), então vai ficar mais ou menos igual ao exemplo abaixo:
```.env
DATABASE_URL="postgresql://POSTGRES_USER:POSTGRES_PASSWORD@localhost:5432/nomeBancoDeDados?schema=public"
```