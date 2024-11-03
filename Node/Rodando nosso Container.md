___
- Para rodar o nosso container `docker`, vamos executar o seguinte comando:
```sh
docker run -p 3333:3333 nome/id
```
- `-p` -> serve para fazer o mapeamento de portas; Passamos a porta que demos `EXPOSE`, no nosso arquivo `Dockerfile` e a porta na qual queremos que em nossa máquina rode essa imagem;
- No lugar de `nome`, podemos passar tanto o nome da imagem como o ID da imagem que queremos que rode.