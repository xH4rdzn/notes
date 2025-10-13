___
- No [Docker Hub](https://hub.docker.com/), é onde fica o `Container Registry`, é onde fica todas as imagens do docker;
- Quando estamos trabalhando com o Docker em uma aplicação é muito comum subirmos duas imagens, uma imagem com a versão `latest`e a outra com uma versão *fixa* que utilizamos;
- O comando `docker pull`, serve para baixar as imagens para o computador;
```zsh
docker pull ubuntu
```
*No comando acima, estamos baixando a imagem do ubuntu*
- Para listar as imagens que possuímos em nosso computador usamos o comando `docker images`
```zsh
docker images
```
 - Quando criamos um container ele vai baixar uma imagem, essa imagem vai vir do `Container Registry`;
 - Para remover uma imagem usamos o comando `docker rmi`e passamos o nome da imagem;
```zsh
docker rmi php
```
*No comando acima, estamos removendo a imagem do PHP*;
- E podemos também apagar uma imagem com uma tag especifica, como no exemplo abaixo que apagamos a versão `latest`do `PHP`
```zsh
docker rmi php:latest
```
