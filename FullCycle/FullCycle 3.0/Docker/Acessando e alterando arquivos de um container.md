___
- Usamos a flag `--name`, para dar um nome para o container;
```zsh
docker run --name nginx -d -p 8080:80 nginx
```
- Para acessar esse container, usamos o comando `docker exec`, esse comando possibilita que usamos um comando dentro do nosso container
```zsh
docker exec CONTAINERNAME COMANDO
```
- Como por exemplo, vamos listar os diretórios do container do `nginx` que criamos anteriormente:
```zsh
docker exec nginx ls
```
- Podemos executar qualquer comando, como acessar o `bash`, mas lembrando que *precisamos da flag `-it` para entrar em modo interativo;*
```zsh
docker exec --it nginx bash
```
- Dentro do `nginx`, ele cria arquivos, e podemos achar esses arquivos no seguinte caminho:
```zsh
cd /usr/share/nginx/html/
```
- Lá ele cria dois arquivos o `index.html`, e um outro arquivo. *Nota-se que o arquivo `index.html` é o arquivo mostrado ao acessar a porta em nosso computador*;
- Para editar esse arquivos, precisamos seguir os passos abaixo:
1. Atualizar os arquivos
```zsh
apt-get update
```
2. Instalar o `vim`
```zsh
apt-get install vim
```
3. Após a instalação podemos usar o `vim`, para poder editar o nosso arquivo
```zsh
vim index.html
```
4. Para podermos alterar o arquivo precisamos entrar no modo `insert`, para isso pressionamos a tecla `I`;
5. Após fazer as alterações desejadas nesse arquivo, apertamos a tecla `ESC`, para sair do modo `insert`, e salvamos, para salvar usamos o `:w`
```zsh
:w
```
6. Para sair do `vim`, usamos o comando `:q`
```zsh
:q
```
- *Os containers são imutáveis, então se pararmos esse container, todas as alterações feitas vão ser desfeitas*
- Tudo que gravarmos dentro de um container ao parar ele vai ser perdido;
