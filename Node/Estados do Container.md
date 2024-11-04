___
- Podemos verificar o estado em que o container se encontra, ao usarmos o comando: `docker ps`:
```sh
docker ps
```
- Esse comando retorna uma lista de containers que estão rodando, e o status desses container.
- No caso se estiver `UP`, significa que o container está rodando.
- Podemos pausar o nosso container, para isso usamos o comando:
```sh
docker pause idContainer
```
- Em `idContainer`, passamos o ID do container que queremos pausar;
- Quando um container está pausado, ele não consome processamento;
- Podemos voltar a rodar um container pausado com o comando:
```sh
docker unpause idContainer
```
- Em `idContainer`, passamos o ID do container que queremos *despausar*;
- Podemos também parar a execução desse container, para isso usamos o comando:
```sh
docker stop idContainer
```
- Em `idContainer`, passamos o ID do container que queremos *parar*;
- Para listar todos os container que temos usamos o comando:
```sh
docker ps -a
```
- Se quisermos iniciar o nosso container que demos `stop`, usamos o comando:
```sh
docker start idContainer
```
- Em `idContainer`, passamos o ID do container que queremos *iniciar novamente*;