___
- Vamos utilizar o *VSCode*, então primeiramente precisamos instalar a extensão feita pelo `google`no vscode.
- Após fazer a instalação da extensão vamos usar o atalho: `CTRL + SHIFT + P`e vamos digitar até aparecer a opção: `go: install/update tools`
- Vamos selecionar todas as ferramentas que irão aparecer e apertar em `ok`, após isso só esperar a instalação.
- Agora podemos fazer o nosso primeiro programa. Para fazermos isso navegamos até a pasta que queremos criar o nosso projeto em `GO`.
- E no terminal digitamos o comando:
```zsh
go mod init myFirstGoProject
```
- Agora na raiz do nosso projeto, criamos um arquivo com o nome: `main.go`
- Mas em `Go`a primeira linha do nosso programa precisa ser um `package` que vamos declarar, antes deles apenas comentários.
```go
package main
```
- Quando declaramos o `package main`, o compilador de `Go`sabe que esse arquivo deve se tornar um executável.
- Então agora continuamos:
```go
package main

import "fmt"

func main() {
	fmt.Println("hello world!")
}
```
- Agora para poder rodar o nosso projeto usamos o comando:
```zsh
go run main.go
```
- O comando acima compila o nosso programa, executa e depois joga o executável fora.
- Para compilar o nosso projeto usamos o comando:
```zsh
go build main.go
```
- Podemos buildar o nosso projeto para outros sistemas operacionais, para isso precisamos apenas *setar* uma nova variável ambiente, para fazermos isso usamos o comando:
```zsh
go env -w GOOS=windows
```
- **Não podemos esquecer de voltar para o sistema operacional que realmente estamos usando para não quebrar o nosso ambiente de desenvolvimento**
