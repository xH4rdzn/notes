___
- Como vimos [[Acessando e alterando arquivos de um container|anteriormente]], todas as modificações feitas, ao matarmos esse container, vão ser perdidas;
- Para evitar isso usamos os `bind mounts`, é basicamente montar um volume que está no nosso computador para dentro do container, caso matarmos esse container, o arquivo estará em nosso computador;
- Para podermos montar um volume em nosso container usamos a flag `-v`
```zsh
docker run -d --name nginx -p 8080:80 -v 
```
- `-v` -> Montar o volume
- Após a flag `-v`, precisamos passar o caminho do volume em nosso computador, deixando o comando mais ou menos como no exemplo abaixo:
```zsh
docker run -d --name nginx -p 8080:80 -v ~/Projects/fullcycle2/docker/html/:/usr/share/nginx/html nginx
```
- Após o caminho do volume em nosso computador usamos o `:`, e indicamos o caminho no qual esse voluma irá ser montado no container, neste caso passamos a pasta na qual o `nginx`, tem os arquivos `.html`
```text
~/Projects/fullcycle2/docker/html/:/usr/share/nginx/html
```
- O comando `-v`, é um dos mais antigos do Docker, atualmente usamos a flag `--mount`, deixando o nosso comando da seguinte maneira:
```zsh
docker run -d --name nginx -p 8080:80 --mount type=bind,source="$(pwd)"/
```
- `"$(pwd)"` -> Pega o caminho onde estamos atualmente;