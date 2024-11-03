___
- `CLI` -> Interface de linha de comando.
- Para criar um novo projeto, usamos o comando:
```sh
dotnet new console -n nomeAplicacaoConsole
```
- Para rodar o nosso projeto usamos o comando, quando está na pasta do projeto:
```sh
dotnet run
```
- O comando `build`, pode ser usado nos projetos ou na solução, esse comando verifica se está tudo correto em seu código, mas apenas erros de sintaxe, importações entre outros. E cria os arquivos na linguagem intermediaria.
- O comando `test`, vai rodar todos os testes de unidade;
- O comando `publish`, ele vai preparar o seu código para executar dentro de um servidor;
