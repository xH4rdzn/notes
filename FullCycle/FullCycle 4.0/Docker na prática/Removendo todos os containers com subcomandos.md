___
- Se tivermos muitos containers e quisermos apagarmos todos, podemos fazer combinações de comandos
- Como listar todos os *ID's* dos containers que temos em nossa máquina
```zsh
docker ps -a -q
```
- Então assim podemos apagar todos os containers de uma vez usando o comando abaixo:
```zsh
docker rm -f $(docker ps -a -q)
```
- Podemos usar essa forma de *subcomandos*, para muitas coisas.