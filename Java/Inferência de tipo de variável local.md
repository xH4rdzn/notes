___
- A partir do Java 10, temos uma funcionalidade chamada de inferência de tipo de variável local.
- É quando o compilador ele deduz/infere o tipo de variável que estamos declarando.
- Para fazer fazer isso usamos a palavra-reservada `var` e usamos ela da seguinte maneira:
```java
var nome = "Igor Coelho"; // Tipo String

var Carro = new Carro(); // Tipo Carro -> Classe
```
- Mas quando declaramos as variáveis com `var`, automaticamente precisamos inicializar a variável atribuindo algum valor para ela.
- E também não podemos atribuir o valor de `null`
```java
// Não compila
var visitante;
var nome = null;
```
- **E ela também não funciona em variáveis de instância em objetos**
- Usamos `var`, quando o valor inicial tiver informações o suficiente para poder entendermos o tipo daquela variável.