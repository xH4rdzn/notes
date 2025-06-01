___
- O nome da nossa classe deve ser o mesmo nome do arquivo:
```java
// Arquivo: Calculadora.java

public class Calculadora {}
```
- ***Nota-se que usamos o padrão `PascalCase`, para podermos nomearmos as classes***

### Declarando variáveis
- Para podermos declarar variáveis, podemos seguir como no exemplo abaixo:
```java
Tipo NOmeBemDefinido = Atribuicao;
```
- *A atribuição em alguns casos podem ser opcionais*.
- Alguns exemplos: 
```java
int idade = 26;

int anoFabricacao = 2025;
```
- ***Nota-se que para nomearmos variáveis, usamos o padrão `camelCase`;
- Para nomearmos variáveis com **valores constantes**, usamos o seguinte padrão:
```java
String BR = "Brasil";

double PI = 3.14;
```
- Mas para de fato criarmos variáveis com valores constantes usamos a keyword `final`, como no exemplo a seguir:
```java
final String BR = "Brasil";
```
- Para constantes com nomes compostos, usamos o `_`, para fazer a separação das palavras
```java
final BR_PAIS = "Brasil";
```

### Declaração de Métodos
- Para declarar métodos, usamos como no exemplo abaixo:
```java
TipoRetornpo NomeObjetivoNoInfinitivo(parametros p) {}
```
- Então em java uma declaração de método ficaria assim:
```java
int somar(int numeroUm, int numero2) {}
```
