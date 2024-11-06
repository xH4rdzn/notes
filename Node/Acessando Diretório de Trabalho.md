___
- Podemos acessar o diretório de trabalho do nosso container, para poder ver os arquivos, para isso usamos o comando abaixo:
```bash
docker exec -it idContainer bash
```
- Trocamos o `idContainer` pelo ID, do container que queremos acessar o diretório de trabalho;
- Se usarmos outro terminal como o `zsh`, passamos da seguinte maneira:
```bash
docker exec -it idContainer //bin/sh
```
- Desta maneira vamos acessar o diretório de trabalho, e podemos navegar por ele;