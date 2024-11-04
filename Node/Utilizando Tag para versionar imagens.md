___
- Para poder usar a Tag para versionar as imagens de nossos container, ao criar passamos o versionamento da seguinte maneira:
```sh
docker build -t api:v1 .
```
- E agora podemos usar essas versões para criar um container, com uma versão especifica para isso usamos o comando da seguinte maneira:
```sh
docker run -p 3333:3333 -d api:v2
```
- O comando acima vai usar a imagem com nome de `api`, porém em sua `v2`;