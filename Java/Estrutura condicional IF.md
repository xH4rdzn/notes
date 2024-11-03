___
- Para criarmos uma estrutura condicional `if`, fazemos da seguinte maneira:
```java
if (condicao) {
	// Código caso verdadeiro
}
```
- Caso a condição resulte em `true`, o código dentro do bloco será executado.
- Podemos também fazer com que ele execute um bloco de código, caso a condição seja `false`.
```java
if (condicao) {
	// Código caso verdadeiro;
} else {
	// Código caso falso;
}
```
- Ainda também, podemos passar múltiplas condições, da seguinte maneira:
```java
if (condicao) {
	// Código caso verdadeiro
} else if (outraCondicao) {
	// Código caso outra condição seja verdadeira
} else {
	// Código caso nenhuma das condições for verdadeira
}
```
- Podemos ter quantos `else if`, precisarmos;