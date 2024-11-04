___
- Para executarmos o Docker em background, em outras palavras deixar o terminal livre após executar o nosso container, devemos usar o comando abaixo:
```sh
docker run -p 3333:3333 -d api
```
- Passamos a flag `-d`, assim o nosso container vai ficar rodando em background.