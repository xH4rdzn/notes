___
- Para escrever na tela um texto qualquer
- **Sem quebra de linha ao final:**
```java
System.out.print("Bom dia!");
```
- **Com quebra de linha ao final:**
```java
System.out.println("Bom dia!");
```
- Para escrever o conteúdo de uma variável de algum tipo básico, fazemos como no exemplo abaixo:
```java
int y = 32;

System.out.println(y);
```
- Para escrever o conteúdo de uma variável com ponto flutuante:
```java
double x = 10.35784;

System.out.println(x);

System.out.printf("%.2f%n", x);
System.out.printf("%.4f%n", x);
```
- Usamos o `printf`, para formatar a nossa impressão;
- Para especificarmos que queremos duas casas decimais usamos o padrão -> `%.2f%n`, se quisermos quatro casas decimais trocas o `2`por `4`;
- Para podermos definirmos o separador de casas decimais dos Estado Unidos, fazemos o seguinte:
```java
import java.util.Locale;

Locale.setDefault(Locale.US);
```
- Para concatenar vários elementos em um mesmo comando de escrita usamos o `+`, como no exemplo abaixo:
```java
System.out.println("Resultado = " + x + "Metros");
```
- Para concatenar vários elementos em um mesmo comando de escrita, usando o `printf`, seguimos como no exemplo abaixo:
```java
System.out.printf("RESULTADO = %.2f metros%n", x);
```
- Para concatenar vários elementos de tipos diferentes com o `printf`, fazemos como no exemplo abaixo:
```java
String nome = "Igor";
int idade = 26;
double renda = 3500.0;
System.out.printf("%s tem %d anos e ganha R$ %.2f reais%n", nome, idade, renda);
```
- `%f`-> ponto flutuante;
- `%d`-> inteiro;
- `%s`-> texto;
- `%n` -> quebra de linha;
- As variáveis devem ser passadas na ordem que serão exibidas;