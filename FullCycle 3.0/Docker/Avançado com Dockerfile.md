___
- `WORKDIR`-> Passamos o diretório que vamos trabalhar dentro do container;
```dockerfile
WORKDIR /app
```
- `RUN` -> Para rodarmos comandos, podemos passar `&&`para rodar mais de um comando, se tivermos muitos comandos podemos passar a `\`
```dockerfile
RUN apt-get update && apt-get install vim -y
```
- Usando a `\`
```dockerfile
RUN apt-get update && \
	apt-get install vim -y
```
- `COPY`-> Podemos copiar arquivos, inclusive arquivos do nosso computador local para o dentro do container, como no exemplo abaixo:
```dockerfile
COPY html /usr/share/nginx
```