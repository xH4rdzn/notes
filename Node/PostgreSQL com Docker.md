___
- Para poder rodar o *PostgreSQL* com *Docker* na nossa imagem, podemos usar o comando abaixo:
```zsh
docker run --name api-solid-pg -e POSTGRESQL_USERNAME=docker -e POSTGRESQL_PASSWORD=docker -e POSTGRESQL_DATABASE=apisolid -p 5432:5432 bitnami/postgresql
```
- `--name`-> Como queremos chamar esse serviço em nossa máquina.
- `-e`-> Para definirmos variáveis ambiente.
- Agora para configurar a nossa aplicação com o nosso banco de dados, vamos no arquivo `.env`e alteramos a `DATABASE_URL`com as informações passadas na hora em que criamos o container:
```.env
DATABASE_URL="postgresql://docker:docker@localhost:5432/apisolid
```
- E para testar podemos usar o comando:
```zsh
npx prisma migrate dev
```
- O comando acima vai rodar as migrations, para o nosso banco de dados.