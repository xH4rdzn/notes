___
- Para concatenar textos, usamos o operador `+`, porém se tiver um texto antes  de um calculo, ele irá concatenar os números também:
```java
System.out.println("Resultado:" + x + y);
```
- As variáveis `x` e `y`, vão ser concatenadas e não feito o calculo aritmético, entre as duas variáveis.
- Mas, da maneira abaixo, iria ser feito o calculo normalmente:
```java
System.out.println(x + y + " foi o resultado");
```
- Se quisermos fazer o calculo, após uma `string`, usamos o `()`.
```java
System.out.println("Resultado: " + (x + y));
```
- Para declarar uma variável do tipo texto, fazemos da seguinte maneira:
```java
String nome = "Maria";
```
- Nota-se que diferente das variáveis numéricas, o tipo `String`, tem sua letra inicial maiúscula, pois no java, `String` não é um tipo primitivo, Então usa-se a classe `String`; 