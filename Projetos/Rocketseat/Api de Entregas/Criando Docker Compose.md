___
- Para criarmos os containers que vamos utilizar nesse projeto, vamos utilizar o `Docker Componse`, como vimos [[Criando o Docker Compose|anteriormente]], ele serve para subir vários containers com apenas um único comando.
- Para fazer isso então, na raiz do nosso projeto, vamos criar o arquivo `docker-compose.yml`
- E fazer como no exemplo abaixo:
```yml
service:
	postgres:
		image: "bitnami/postgresql:latest"
		ports:
			- "5432:5432"
		environment:
			POSTGRES_USER: postgres
			POSTGRES_PASSWORD: postgres
			POSTGRES_DB: rocketlog
```

