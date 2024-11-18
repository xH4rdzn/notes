___
- Para criar uma imagem docker, usamos o arquivo `Dockerfile`, esse arquivo tem o *passo-a-passo* para criar a nossa imagem docker;
```dockerfile
FROM nomeDaImagem:tag

RUN apt-get update
RUN apt-get install vim -y
```
- Abaixo a explicação dos comandos:
	- `FROM` -> A partir de qual imagem existente vamos começar o nosso container;
	- `RUN` -> Rodar um comando dentro da imagem que passamos no `FROM`;
- Agora para buildar o nosso container a partir desse arquivo, usamos o seguinte comando:
```zsh
docker build -t usuarioDockerHub/nomeImagem:Versao .
```
0 `.` diz para o docker que é para buscar o `Dockerfile`na pasta onde estamos;