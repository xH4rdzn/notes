___
- O `Dockerfile` é um arquivo onde vamos definir a imagem que vamos utilizar e as características necessárias para executar nossa aplicação. Seguindo os passos abaixo:
1. Na raiz do nosso projeto vamos criar um arquivo com o nome `Dockerfile`
2. Dentro desse arquivo vamos escrever um código com o passo a passo, como no exemplo a seguir:
```Dockerfile
FROM node:18-alpine3.20

WORKDIR /usr/src/app

COPY . .

RUN npm install

RUN npm run build

EXPOSE 3333

CMD ["npm", "start"]
```
- `FROM`-> Esse comando determina a imagem que vamos utilizar como base
- `WORKDIR`-> Indicamos o diretório de trabalho
- `COPY` -> Copiar os arquivos
- `. . `-> Representa que queremos copiar todos os arquivos e colocar eles todos dentro da nossa pasta que estamos utilizando como diretório de trabalho
- `RUN` -> Serve para executarmos um comando
- `EXPOSE`-> Serve para expor a porta que o container vai utilizar para fazer a comunicação.
- `CMD []`-> Serve também para rodarmos um comando, porém podemos passar as palavras do comando de maneira separada, como em um *array*