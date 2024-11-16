___
- `docker volume ls` -> Esse comando serve para listar todos os volumes criados;
```zsh
docker volume ls
```
- Para criar um volume usamos o comando `docker volume create nomeVolume`
```zsh
docker volume create meuVolume
```
- Para listar informações do volume que criamos, usamos o comando `docker volume inspect nomeVolume`
```zsh
docker volume inspect meuVolume
```
- A propriedade `Mountpoint`, é o caminho onde vai ficar os arquivos em nosso computador;
- E agora para montar o volume em nosso container usamos o `--mount` da seguinte maneira:
```zsh
docker run --name nginx -d --mount type=volume,source=meuvolume,target=/app nginx
```
- Conseguimos usar o mesmo volume para vários containers;
- Se usamos o comando `-v`, podemos passar o volume também da seguinte maneira:
```zsh
docker run --name nginx3 -d -v meuvolume:/app nginx
```
- Podemos apagar todos os volumes que não estão sendo usados com o comando `docker volume prune`
```zsh
docker volume prune
```