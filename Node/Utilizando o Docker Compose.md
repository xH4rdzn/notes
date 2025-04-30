____
- O Docker Compose, é um arquivo que criamos na raiz do nosso projeto, e esse arquivo dita quais containers precisamos criar para rodar a nossa aplicação.
- Para isso criamos na raiz do nosso projeto o arquivo `docker-compose.yml`
- E dentro dele fazemos:
```yml
services:
	api-solid-pg:
		image: bitnami/postgresql
		ports:
			- 5432:5432
		environment:
			- POSTGRESQL_USERNAME=docker
			- POSTGRESQL_PASSWORD=docker
			- POSTGRESQL_DATABASE=apisolid
```
- Agora para poder subir esse container usamos o comando:
```zsh
docker compose up -d
```
- Quando quisermos parar de executar os container usamos o comando:
```zsh
docker compose stop
```