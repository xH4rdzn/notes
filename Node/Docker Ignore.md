___
- Esse arquivo serve para dizer ao `Docker`, quais pastas ele deve ignorar
- Na raiz do nosso projeto criamos um arquivo com o nome: `.dockerignore`
- E dentro desse arquivo colocamos o que queremos ignorar:
```.dockerignore
node_modules
dist
Dockerfile
.git
.dockerignore
.gitignore
```
- Esses arquivos, não vão para o nosso container; 