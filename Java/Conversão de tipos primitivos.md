___
- `Casting` -> Conversão
- Usamos o `casting`, quando queremos mudar o tipo da variável, para outro tipo primitivo.
- Para fazer o `casting`, fazemos da seguinte maneira:
```java
long x = 10;
int y = (int) x;
```
- O `casting`, tem que ser usado de forma cautelosa, uma vez que pode-se perder dados. Principalmente quando se passa de um tipo com maior capacidade, para um tipo com menor capacidade.
- O caso contrario, passar de um tipo de menor capacidade, para um tipo de maior capacidade, ele ocorre de maneira implícita/automática.
```java
int a = 12543;
long b = a;
```