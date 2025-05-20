___
### Scanner
- Para fazer entrada de dados, nós vamos criar um objeto do tipo "Scanner" da seguinte forma:
```java
import java.util.Scanner;

Scanner sc = new Scanner(System.in);
```
- Quando não precisar mais do objeto *Scanner*, usamos o comando:
```java
sc.close();
```
- Para ler uma palavra *texto sem espaços*
```java
Scanner sc = new Scanner(System.in);

String x;

x = sc.next();
```
- Para ler um número inteiro
```java
Scanner sc = new Scanner(System.in);

int x;

x = sc.nextInt();
```
- Para ler um número com ponto flutuante
```java
Scanner sc = new Scanner(System.in);

double x;

x = sc.nextDouble();
```
- *Para considerar o separador de decimais como ponto, **antes** da declaração do Scanner faça*:
```java
Locale.setDefault(Locale.US);
```
- Para ler um caractere
```java
Scanner sc = new Scanner(System.in);

char x;

x = sc.next().charAt(0);
```
- Para ler vários dados na mesma linha fazemos como no exemplo abaixo:
```java
Scanner sc = new Scanner(System.in);

String x;
int y;
double z;

x = sc.next();
y = sc.nextInt();
z = sc.nextDouble();
```
- Desta maneira em apenas uma linha conseguimos inserir vários dados, separando eles apenas por espaço.
- Para ler um texto *até a quebra de linha*:
```java
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);

		String s1, s2, s3;

		s1 = sc.nextLine();
		s2 = sc.nextLine();
		s3 = sc.nextLine();

		System.out.println(s1);
		System.out.println(s2);
		System.out.println(s3);
	}
}
```
- **Atenção**: quebra de linha pendente, ao usarmos qualquer método diferente do `nextLine`, ele fica com uma quebra de linha pendente, para solucionar isso, adicionamos um `nextLine()`, antes de onde queremos armazenar aquele dado.
```java
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);

		int x;
		String s1, s2, s3;

		x = sc.nextInt();
		sc.nextLine();
		s1 = sc.nextLine();
		s2 = sc.nextLine();
		s3 = sc.nextLine();

		System.out.println(x);
		System.out.println(s1);
		System.out.println(s2);
		System.out.println(s3);
	}
}
```