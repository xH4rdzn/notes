___
- É uma maneira alternativa para a estrutura [[Estrutura condicional IF|if/else]];
- Usamos como no exemplo abaixo:
```java
double valorImpostos = tipoNota == "s" ? totalFaturado * 0.16 : totalFaturado * 0.35;
```
- Podemos ter um ternário, dentro de outro, porém não é recomendado.
```java
String variavel = condicao ? casoTrue : casoFalse;
```