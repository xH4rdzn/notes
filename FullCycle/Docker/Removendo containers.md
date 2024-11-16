___
- `docker stop containerId/name` -> Esse comando para o container que é passado para ele pelo `CONTAINER ID` ou pelo `NAME`;
```zsh
docker stop containerId
```
- `docker start containerId` -> Esse comando serve para que o container inicie;
```zsh
docker start containerId
```
- Para podermos remover o container da nossa máquina, usamos o comando `docker rm` e passamos o `CONTAINER ID`, para que apague aquele container;
```zsh
docker rm containerId
```
- Ou podemos apagar o container pelo `NAME`, assim usamos o mesmo comando só passamos o `NAME` do container:
```zsh
docker rm containerName
```
- *Não podemos remover um container que está com o status `UP`*
- Mas se não quisermos parar esse container podemos passar a flag `-f`, para forçar a remoção desse container;
```zsh
docker rm containerName -f
```