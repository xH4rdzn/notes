___
- Para declarar uma função usamos a *keyword*: `func`
```go
// Declarando uma função
func digaOi(){
	fmt.Println("oi")
}
```
- Agora para chamar essa função chamamos ela com o nome:
```go
func main() {
	digaOi()
}
```
- As funções podem receber parâmetros e devolver algo, como no exemplo abaixo:
```go
func somar(a int, b int) int {
	return a + b
}
```
- Quando os tipos dos parâmetros são iguais, podemos omitir o tipo
```go
func somar(a, b int) int {
	return a + b
}
```
- Em `Go`, as funções podem devolver mais de um resultado, como demostrado no exemplo abaixo:
```go
func swap(a, b int) (int, int) {
	return b, a
}
```
- Podemos dar nomes para essas variáveis que estamos retornando
```go
func dividir(a, b int) (int, int) {
	res := a / b
	rem := a % b
	return res, rem
}

// Poderiamos dar os nomes diretamente na declaração
func dividir(a, b int) (res int, rem int) {
	res = a / b
	rem = a % b
	return res, rem
}
```
- Poderíamos fazer um `naked return`, que seria como no exemplo abaixo:
```go
func dividir(a, b int) (res int, rem int) {
	res = a / b
	rem = a % b
	return
}
```
- Significa que estamos retornando o que foi declarado como retorno.
- Também temos o que chamamos de funções `high order`, que são funções que retornam outra função, como no exemplo abaixo:
```go
func somar(a int) func(int) int {
	return func(b int) int {
		return a + b
	}
}
```
- Temos também o que chamamos de funções variaticas , essas funções podem receber um número variável de argumentos. Para fazermos isso seguimos o exemplo abaixo:
```go
func somar(nums ...int) int {
	var out int
	for _,n := range nums {
		out += n
	}
	return out
}
```
- O argumento variatico deve ser o último argumento da função
