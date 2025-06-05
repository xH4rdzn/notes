___
- Temos duas maneiras de trabalharmos com persistências de dados em containers.
- Que são *Bind mounts* e *Volumes*;

### O que são *Bind Mounts* ?
- Os *Bind Mounts* basicamente estamos pegando uma pasta do nosso computador e estamos mapeando ela para o nosso **container**.
- Nesse caso estamos compartilhando arquivos entre a **Máquina Host** e o **Container**. Que dependendo do sistema é uma máquina virtual (Windows e MacOs).
- O *Volume* é gerenciado pelo ***Docker***, diferente do Binds Mounts a pasta não é compartilhada com a máquina *HOST*. Evitando assim problemas de segurança.
- Geralmente usamos *Volumes*, quando estamos trabalhando com banco de dados, e em produção.
- Em outras palavras:
- ***Bind Mounts*** -> usamos para ambientes de desenvolvimento, e quando queremos ter acesso aos arquivos.
- ***Volumes*** -> pasta que não queremos ter acesso e para ambiente de produção.
