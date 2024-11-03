___
- Para declararmos um tipo `wrapper`, não precisamos usar o método `valueOf`, podemos simplesmente dar o valor para o `wrapper`;
- E o compilador automaticamente, faz de maneira automática o que chamamos de `autoboxing`; 
- Como no exemplo abaixo que estamos declarando um `Integer`:
```java
Integer diasEntrega = 30;
```
- E o `unboxing` é quando queremos tirar o tipo primitivo de dentro do `wrapper`, e para fazermos isso podemos seguir o exemplo:
```java
// unboxing
Integer diasEntrega = 30;
int diasEntregaInt = diasEntrega;
```
- Não precisamos usar o método de conversão como `intValue()`;