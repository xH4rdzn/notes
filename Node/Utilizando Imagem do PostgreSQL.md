___
- Para criarmos um container utilizando a imagem do PostgreSQL, acessamos o site do [Docker Hub](https://hub.docker.com/r/bitnami/postgresql), e procuramos a imagem do PostgreSQL que queremos usar, neste exemplo vamos usar a imagem da `bitnami`.
- E então no terminal digitamos o seguinte comando:
```sh
docker run --name db-postgres -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=postgres -p 5342:5432 -d bitnami/postgresql:latest
```
- `--name` -> passamos um nome para a imagem;
- `-e` -> variáveis de ambiente;
- `-p`-> para mapear as portas;
- Após o `-d`, passamos a imagem que queremos usar;
- Após executar o comando do exemplo, vamos ter um novo container rodando a imagem do `postgresql`;