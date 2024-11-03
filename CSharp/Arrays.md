___
- Os Arrays, servem para guardar vários valores de um tipo, para fazer a sua declaração seguimos o exemplo abaixo:
```c#
int[] inteiros = new int[10];
```
- Para declarar um array seguimos: `tipo do array[] nomeVariavel = new tipo do array[tamanhoDoArray];`
- Os Arrays, é uma coleção com tamanho fixo.
- Para armazenar um valor em um array podemos fazer da seguinte maneira:
```c#
inteiros[0] = 1;
```
- Lembrando que um array, começa na posição 0.
- Para pegar o valor de uma posição passamos:
```c#
Console.WriteLine(inteiros[0]);
```
- Quando temos certeza dos elementos que vão estar no array, podemos inicializar ele da seguinte forma:
```c#
int[] inteiros = [1, 10, 7];
```
- Mas no exemplo acima, já é inferido o tamanho do array.
- Podemos ter arrays com colunas e linhas para declarar um array desta maneira fazemos como no exemplo abaixo:
```c#
int[,] inteiros = new int[10, 10];
```
- No exemplo acima estamos criando um array com 10 linhas e 10 colunas;