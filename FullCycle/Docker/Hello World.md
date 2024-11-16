___
- `docker ps` -> esse comando mostra os containers que estão ativos na sua máquina
```zsh
docker ps
```
- `docker run hello-world` -> esse comando vai rodar a imagem `hello-world`
```zsh
docker run hello-world
```
- *Se não tivermos a imagem o Docker automaticamente vai baixar a imagem na qual rodamos*
- Em outras palavras o comando `docker run`, serve para rodar uma imagem;
```zsh
docker run
```
- `docker ps -a` -> esse comando mostra todos os containers que já rodaram ou estão ativos;
```zsh
docker ps -a
```
- Notamos também que esse comando retorna algumas informações sobre os containers que são:
	- `CONTAINER ID` -> O ID do container
	- `IMAGE` -> A imagem que o container rodou ou está rodando;
	- `COMMAND`-> Algum comando que foi executado pelo container;
	- `CREATED` -> O tempo que o container foi criado;
	- `STATUS` -> Mostra o status em que o container se encontra e o tempo;
	- `PORTS` -> Mostra as portas usadas pelo container;
	- `NAMES` -> Um nome para o container, se não dermos um nome, gera um nome aleatório;