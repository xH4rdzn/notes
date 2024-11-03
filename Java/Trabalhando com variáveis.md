___
- Para declarar uma variável em java, precisamos primeiro definir o tipo.
- Depois o nome, que vamos dar para a variável.
```
<tipo> <nomeDaVariável>;
```
- Como por exemplo:
```java
int minhaIdade;
```
- Depois de declarada, a variável não pode ter seu tipo alterado;
- Para atribuir um valor para a variável usamos o sinal de `=`
```java
int minhaIdade;
minhaIdade = 26;
```
- Se quisermos mostrar o valor da variável no console, usamos o `System.out.println`
```java
int minhaIdade;
minhaIdade = 26;
System.out.println(minhaIdade);
```
- Podemos também declarar e atribuir um valor para a variável:
```java
int minhaIdade = 26;
```
- Para alterar o valor da variável, chamamos ela e atribuímos um novo valor
```java
minhaIdade = 27;
```
- Podemos usar as variáveis para realizar cálculos, a partir de valores de outras variáveis
```java
int minhaIdade = 26;
int suaIdade = 20;
int totalIdades = minhaIdade + suaIdade;
System.out.println(totalIdades);
```
- Variáveis do mesmo tipo, podem ser declaradas e atribuídas, apenas em uma linha
```java
int minhaIdade = 26. suaIdade = 20;
```