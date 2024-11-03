___
- Usamos esse método, quando queremos devolver uma saída formatada.
- `%s` -> vai ser trocado pelo valor de uma variável do tipo `String`
```java
System.out.printf("Olá, %s", variavel);
```
- `%n` -> quebra de linha
- `%d` -> É trocado pelo valor de uma variável numérica do tipo inteiro`int, long`
```java
int minhaIdade = 26;
System.out.printf("Olá, Igor, sua idade é: %d", minhaIdade);
```
- `%f` -> É trocado por uma variável do tipo ponto flutuante `double ou float`
```java
double meuSaldo = 340.55131;
System.out.printf("Seu saldo é de: %f", meuSaldo);
``` 
- Para especificar a quantidade de casas decimais fazemos da seguinte maneira:
```java
double meuSaldo = 340.55131;
System.out.printf("Seu saldo é de: %.2f", meuSaldo);
```
