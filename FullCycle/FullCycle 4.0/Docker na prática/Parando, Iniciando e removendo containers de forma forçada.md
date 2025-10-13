___
- Para podermos remover os containers que foram criados temos duas maneiras de fazer isso.
- Uma delas é usando o comando `docker rm`e passamos o *ID* do container:
```zsh
docker rm 236718362
```
- Outra maneira é usando o mesmo comando porém passamos o nome do container:
```zsh
docker rm meuContainer
```
- Porém toda vez que formos remover um container, o mesmo não pode estar rodando.
- Em outras palavras ele precisar estar parado ou com o status de `EXITED`.
- Se quisermos remover um container que está com o status `UP`, podemos parar o container usando o comando:
```zsh
docker stop ID
```
- Ou podemos parar pelo nome também:
```zsh
docker stop meuContainer
```
- Mas se não quisermos parar o container e mesmo assim quisermos remover usamos o comando da seguinte maneira:
```zsh
docker rm -f meuContainer
```
- Para executar esse container novamente podemos usar o comando `docker start`, podemos passar tanto o *ID* como o *nome* do container:
```zsh
docker start meuContainer
```
- **O comando `start`diferente do `run`, não cria um novo container, mas sim executa um container que está parado**
- 