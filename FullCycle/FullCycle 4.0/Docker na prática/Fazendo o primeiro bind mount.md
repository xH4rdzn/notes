___
- Para podermos mapear uma pasta do nosso computador para um *container*, podemos usar um parâmetro no momento de criação do mesmo, como é demonstrado no exemplo abaixo:
```zsh
docker run -d -p 8080:80 -v $(pwd)/my_paste:/usr/share/nginx/html/ nginx
```
- O `-d` é para rodar em modo [[Attach e dettach|dettach]];
- O `-p` é para podermos fazer o [[Publicando portas|mapeamento de portas]] do nosso computador para o container;
- O `-v`é onde indicamos o o caminho absoluto da pasta que queremos montar dentro do nosso container
- O `$(pwd)` é um atalho para o caminho absoluto, é usado para quando estamos trabalhando dentro da pasta que queremos montar dentro do nosso container;
- Dessa maneira todos os arquivos que gerarmos em nosso computador, será passada para o nosso *container* que está rodando o `nginx`;
- Caso removermos esse container não vamos perder os arquivos, uma vez que os arquivos estão em nosso computador local;