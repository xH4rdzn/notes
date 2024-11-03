___
- `docker ps` -> esse comando lista os container em execução
```sh
docker ps
```
- `docker image ls` -> esse comando lista as imagens que temos baixadas
```sh
docker image ls
```
- `docker build -t nomeDaNossaImagem .` -> Esse comando serve para baixar as imagens vamos utilizar, nesse caso ele vai procurar o arquivo `Dockerfile`, e vai seguir as instruções contidas nesse arquivo; Em `nomeDaNossaImagem`, demos o nome que quisermos, só não podemos usar espaços;
```sh
docker build -t api .
```
- Com o comando acima, já vamos baixar a imagem que passamos para o `Dockerfile`, mas nosso container ainda não vai estar rodando, para isso vamos seguir [nessa outra nota](./Rodando%20nosso%20Container.md)