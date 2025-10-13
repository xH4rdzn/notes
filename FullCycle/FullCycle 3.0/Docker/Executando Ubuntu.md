___
- Ao rodarmos o [[Hello World]], ele nos pediu para tentar rodar um comando:
```zsh
docker run -it ubuntu bash
```
- `docker run` -> Serve para rodarmos uma imagem/container;
- `-i` -> Modo interativo;
- `-t` -> TTY -> Serve para podermos digitar comandos no nosso terminal;
- `ubuntu` -> A imagem que queremos rodar, se não passamos nenhuma versão automaticamente ele vai buscar a última versão. Se quisermos uma versão especifica usamos `:` e passamos a versão;
- `bash` -> É comando que queremos executar na imagem;
- Para podermos sair do container que está rodando em modo interativo, usamos o comando `exit`, no terminal em que está rodando o container em modo interativo
```zsh
exit
```
- Se quisermos subir um container apenas para executar um comando, podemos utilizar a flag `--rm`, assim ele vai subir o container e assim que sairmos dele, ele irá remover da máquina;
```zsh
docker run -it --rm ubuntu bash
```


