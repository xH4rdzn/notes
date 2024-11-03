___
- Para podermos receber dados do usuário, usamos a classe `Scanner`
- Usamos da seguinte maneira:
```java
Scanner entrada = new Scanner(System.in);
```
- Não podemos esquecer de importar o pacote do `Scanner`
```java
import java.util.Scanner;
```
- Usamos métodos diferentes, para cada tipo de dado que vamos receber:
	- `nextLine()` -> usado para `strings`;
	- `nextInt()` -> usado para números inteiros;
	- `nextDouble()` -> usado para números de ponto flutuante;
- Quando usamos os métodos `nextInt()` e `nextDouble()`, eles não consome a quebra de linha, sendo assim pulando a próxima entrada, para resolver isso, após esses métodos, usamos o `nextLine()`, para resolver esse problema.