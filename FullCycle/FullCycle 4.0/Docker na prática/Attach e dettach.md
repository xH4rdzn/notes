___
- Ao executarmos um container, em algumas imagens ela irá deixar o terminal bloqueado, desta maneira não podemos executar outros comandos.
- Mas as vezes queremos que fique desta maneira, mas na maioria das vezes não.
- Mas para podermos executarmos o container e deixar o terminal livre usamos o `-d`
```zsh
docker run -d nginx
```
- O `-d`significa **dettach**;
- Podemos voltar a ver os logs, usando o comando da seguinte maneira:
```zsh
docker attach meuContainer
```