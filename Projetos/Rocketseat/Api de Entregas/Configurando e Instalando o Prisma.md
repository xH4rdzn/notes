___
- Como vamos utilizar o `ORM`Prisma, vamos instalar ele da seguinte maneira:
```zsh
npm i prisma -D
```
- Após a instalação, vamos executar o seguinte comando:
```zsh
npx prisma init --datasource-provider postgresql
```
- Após isso será gerado um arquivo `.env`, e precisamos alterar as informações, para as informações que passamos no nosso arquivo [[Criando Docker Compose|Docker Compose]];
```.env
# Sem alterações
DATABASE_URL="postgresql://johndoe:randompassword@localhost:5432/mydb?schmea=public"

# Com as alterações
DATABASE_URL="postgresql://postgres:postgres@localhost:5432/rocketlog?schmea=public"
```
*Nota-se que alterações as informações  que devem ser mudadas são: `johndoe`, `randompassword` e`mydb`, e elas são informações que passamos no arquivo do `DOCKER COMPOSE`;
- Precisamos também que esse arquivo `.env`, esteja disponível, quando formos executar a nossa aplicação, para isso voltamos ao arquivo `package.json`e alteramos o script de `dev`, para o seguinte:
```json
"dev": "tsx watch --env-file .env src/server.ts"
```
- Como não devemos subir o arquivo `.env`, para o *GitHub*, podemos criar uma cópia dele com o nome de `.env-example`, e nele passamos apenas as variáveis, sem valores, como no exemplo abaixo:
```env
DATABASE_URL=
```
*O arquivo `.env-example`, pode subir para o GitHub;*

