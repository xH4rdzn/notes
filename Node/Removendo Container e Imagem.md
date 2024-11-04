___
- Para remover um container ou imagem usamos o comando:
```sh
docker rm idContainer
```
- Em `idContainer`, passamos o ID do container que queremos apagar
- Para poder remover um container precisamos parar ele, ou então podemos forçar uma remoção.
- Para apagar forçando usamos o comando abaixo:
```sh
docker rm -f idContainer
```
- Em `idContainer`, passamos o ID do container que queremos apagar.
- Para remover uma imagem usamos o comando:
```sh
docker rmi ImageID
```
- Em`ImageID`, passamos o ID da imagem que queremos apagar;