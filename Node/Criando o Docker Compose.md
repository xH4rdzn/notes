___
- Para criamos o nosso Docker Compose, na raiz do nosso projeto vamos criar o arquivo: `docker-compose.yml`;
- Esse arquivo deve ser incluído no arquivo: `.dockerignore`
- Dentro do arquivo: `docker-compose.yml`, vamos cria-lo da seguinte maneira:
```yml
version: "3.9"

services:
	api:
		build:
			context: .
			dockerfile: Dockerfile
		image: nodejs
		container_name: api
		ports:
			- "3333:3333"
		depends_on:
			- postgres
	postgres:
		image: "bitnami/postgresql:latest"
		container_name: postgres
		ports:
			- "5432:5432"
		environment:
			POSGRES_USER: postgres
			POSTGRES_PASSWORD: postgres
			POSTGRES_DB: api
		volumes:
			- database: /var/lib/postgresql/data
volumes:
	database:
```
- `context`-> O contexto é para usar a raiz do nosso projeto como referencia, para a raiz passamos o `.`;
- `dockerfile` -> Passamos o nome do arquivo `Dockerfile`;
- `image` -> passamos o nome que queremos para a imagem;
- `container_name`-> passamos o nome que queremos para o container;
- `ports` -> fazer o mapeamento de portas;
- `depends_on` -> Onde dizemos que esse container depende de outro container, e passamos o nome de outro serviço;
- `environment` -> Definimos as variáveis de ambiente do serviço;
	- `POSTGRES_USER` -> definimos o usuário do banco de dados;
	- `POSTGRES_PASSWORD` -> Definimos a senha do banco de dados;
	- `POSTGRES_DB`-> Definimos o nome do banco de dados;
- Em `volumes`, definimos apenas o nome do volume que vamos usar, o caminho tem que ser igual ao do exemplo acima;
- 