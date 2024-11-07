___
- Para conectar com o `Beekeeper`, que é a ferramenta de banco de dados que estamos utilizando, vamos fazer da seguinte maneira:
1. Abrimos o `Beekeeper`, e fazemos uma nova conexão
2. Escolhemos a opção `Postgres`, e alteramos as configurações necessárias;
	- `User` -> passamos a variável ambiente(`POSTGRES_USER`) configurada na criação do container;
	- `Password` -> passamos a variável ambiente(`POSTGRES_PASSWORD`) configurada na criação do container;
3. Após fazer isso é só testarmos a conexão, se tudo ocorrer bem conectamos;