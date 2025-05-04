___
- Para declarar uma variável usamos a *keyword*: `var`.
- Podemos declarar uma lista de variáveis depois da palavra `var`
```go
package main


func main() {
	// Declarando mais de uma variável
	var nome, sobrenome string
}
```
- Podemos também declarar ela fora do escopo da função, chamamos essas variáveis de **globais**
```go
package main

var idade int

func main() {
	// Declarando mais de uma variável
	var nome, sobrenome string
}
```
- Por padrão todas as variáveis em `go`vem zeradas
- No caso de uma variável do tipo `int`o seu valor inicial é 0.
- No caso de uma `string`é uma *string* vazia.
- No caso de um `boolean`é o valor *false*
- Mas se quisermos podemos definir um inicializador para as variáveis
```go
package main


func main() {
	// Inicializando uma variável com um valor.
	var nome, sobrenome = "Igor", "Coelho"
}
```
- Podemos agrupar as variáveis como no exemplo abaixo:
```go
package main


func main() {
	var (
		nome = "Igor"
		sobrenome = "Coelho"
	)
}
```
- Temos outra maneira de declarar variáveis sem usar a *keyword* `var`, como no exemplo abaixo:
```go
package main


func main() {
	nome := "Igor"
	sobrenome := "Coelho"
	fmt.Println(nome, sobrenome)
}
```
- Quando usamos o `:=` significa que estamos declarando e definindo o valor dela ao mesmo tempo. E isso só funciona em variáveis de escopo de função
- Se tivermos apenas o `=`,estamos apenas atualizando o valor dela.
- Podemos declarar variáveis de tipos diferentes na mesma linha como no exemplo abaixo:
```go
package main


func main() {
	var foo, bar = "foo", 50
}
```
- E também podemos usar o `:=`;
- Mas não podemos declarar variáveis de tipos diferentes com seus valores zerados.
- Sempre que usarmos o *shorthand* para definir variáveis não podemos definir o tipo, ele é automaticamente inferiddo.