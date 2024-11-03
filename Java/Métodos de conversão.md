___
- Para poder converter uma variável de um tipo primitivo para outro tipo primitivo, é bem simples basta fazermos o que chamamos de `casting`;
- E para fazermos uma conversão em `wrappers`
- Porém uma classe `wrapper`, possui muitos métodos de conversão;
- Como no exemplo abaixo que queremos converter um `Integer` para um `short`:
```java
Integer diasEntrega = Integer.valueOf(30);
short diasEntregaShort = diasEntrega.shortValue();
```
- E existem métodos para os outros tipos primitivos como:
	- `floatValue()` -> converte para `float`;
	- `intValue()` -> converte para `int`;
	- `longValue()`-> converte para `long`;
	- `doubleValue()` -> converte para `double`;
	- E por ai vai.
- E se quisermos mudar para outro `wrapper`, fazemos da seguinte maneira:
```java
Integer diasEntrega = Integer.valueOf(30);
Short diasEntregaShort = Short.valueOf(diasEntrega.shortValue());
```