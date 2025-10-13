___
- Com o comando `docker exec`, conseguimos rodar um comando dentro do container que passamos como parâmetro.
```zsh
docker exec ID comando
```
- Podemos passar dois parâmetros para o `exec`:
	- `-i`-> para rodar o container de forma interativa.
	- `-t`-> para habilitar o teclado em nosso container.
	- **bash** -> para acessar o terminal do container.
```zsh
docker exec -it ID bash
```
-  Podemos passar para o `docker run`a *flag* `--rm`, assim que ele parar ele vai ser removido.
```zsh
docker run --rm -d nginx
```
