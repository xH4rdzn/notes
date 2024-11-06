___
- Para ver os detalhes de um container usamos o comando abaixo:
```bash
docker container inspect idContainer
```
- Para criar um volume, usamos o comando abaixo:
```bash
docker volume create nomeQueQuisermos
```
- Trocamos o `nomeQueQuisermos`, para um nome que acharmos interessante para o projeto.
- Podemos inspecionar o volume com o comando:
```bash
docker volume inspect nomeDoVolume
```
- Para executar um container e passando o volume que queremos usar fazemos da seguinte maneira:
```bash
docker run -v nomeDoVolume:/usr/src/app -p 3333:3333 -d api
```
- Após o nome do volume, passamos o `WORKDIR` que passamos para o container