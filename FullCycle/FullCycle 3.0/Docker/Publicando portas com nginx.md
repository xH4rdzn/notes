___
- O `nginx` é um servidor web;
- Para rodarmos o `nginx`, usamos o comando:
```zsh
docker run nginx
```
- Se abrirmos outro terminal e digitarmos o comando `docker ps`, vamos ver que o container do `nginx`, está rodando e com alguma porta exposta;
- Mas isso não significa que conseguimos acessar, mas se tivermos outro container rodando, esse outro container conseguiria acessar a porta na qual o nosso `nginx` está rodando;
- Para podermos acessar na nossa máquina usamos a flag `-p`, deixando então o nosso comando da seguinte maneira:
```zsh
docker run -p 8080:80 nginx
```
- O comando acima significa:
	- `8080` -> porta na nossa máquina local;
	- `80` -> porta para qual vai ser redirecionado no docker;
- Desta maneira já conseguimos acessar na nossa máquina, usando o endereço:
```text
localhost:PortaPassada
```
- Se usarmos o comando `docker ps`, vamos perceber que a parte de `PORTS`, vai estar de uma maneira diferente, vai mostrar a porta da nossa maquina e a porta para a qual vai ser redirecionada;
- Para rodarmos o `nginx`, e deixar o nosso terminal livre usamos a flag `-d`
```zsh
docker run -d -p 80:80 nginx
```
- *Desta maneira o terminal vai ficar livre para rodarmos outros comandos*
