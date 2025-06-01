___
### Conceito
- É uma ***estrutura de controle*** que permite definir que um certo *bloco de comandos* somente será executado dependendo de uma **condição**.

### Sintaxe da estrutura condicional
- **Simples**
```java
if(condicao) {
	// comando 1
	// comando 2
}
```
- Se a condição para esse bloco for ***falsa*** os comandos que estão no bloco será pulado.
- **Composta**
```java
if(condicao) {
	// comando 1
	// comando 2
} else {
	// comando 3
	// comando 4
}
```
- Caso a condição for **verdadeira** o bloco que está no `if` será executado, se for **falso**, vai ser executado os comandos que estão no bloco `else`.

### E se eu tiver mais de duas possibilidades ?
- Se tivermos outra condição podemos fazer um *encadeamento de estruturas condicionais*, ou podemos usar o `else if`, ficando da seguinte maneira:
```java
if(condicao) {
	// comandos
} else if (condicao2) {
	// comandos
} else {
	// comandos
}
```