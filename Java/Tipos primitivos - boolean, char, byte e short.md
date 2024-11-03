___

| Tipo      | Tamanho(Bits) | Menor Valor | Maior Valor |
| --------- | ------------- | ----------- | ----------- |
| `boolean` | 1             | `false`     | `true`      |
| char      | 16            | 0           | $2^16$ - 1  |
| byte      | 8             | -$2^7$ - 1  | $2^7$ - 1   |
| short     | 16            | -$2^15$     | $2^15$ - 1  |
| int       | 32            | -$2^31$     | $2^31$ - 1  |
| long      | 64            | -$2^63$     | $2^63$ - 1  |
| float     | 32            | -           | -           |
| double    | 64            | -           | -           |
- Declaramos um boolean:
```java
boolean nomeVariavel;
```
- Declarando um char:
```java
char nomeVariavel;
```
- O valor para este tipo deve estar entre aspas simples `'valor'`
```java
char inicialDoNome = 'I';
```
- Os tipos `byte` e `short`, armazenam números inteiros, porém com uma capacidade menor do que o tipo `int`
- `byte` -> valor máximo 127;
- `short` -> valor máximo 32767;
- Acima dos valores máximo, causa um erro de compilação
