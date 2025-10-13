___
- Para podermos nomear um container usamos a flag `--name`, deixando o comando como no exemplo abaixo:
```zsh
docker run --name myContainer hello-world
```
- Se não passarmos essa flag ele vai inferir um nome de maneira automática.
- Se quisermos verificar as flags de um comando especifico usamos como no exemplo abaixo:
```zsh
docker run --help
```
- O comando acima irá aparecer tudo o que podemos passar como parâmetro do `docker run`.
- Se quisermos procurar um comando especifico, podemos usar o comando abaixo:
```zsh
docker run --help | grep name
```
- Ao executar esse comando irá aparecer apenas os comandos que contém a palavra que passamos para o `grep`.
- Algumas vezes precisamos passar muitos parâmetros para a criação do container, podemos passar os parâmetros da seguinte maneira para poder organizar de maneira melhor:
```zsh
docker run --name=myContainer2 --param=1 --param=2 imagem
```
- *Desta maneira deixa um pouco mais visível o que é parâmetro e o que é imagem.*
- Podemos também passar o comando que esse container vai rodar ao ser executado, como demostrado no exemplo abaixo:
```zsh
docker run --name meuContainer imagem comando
```
- O que está a frente do nome da imagem é o comando que queremos que ele rode ao ser executado.