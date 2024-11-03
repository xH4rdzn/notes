___
- Para declarar uma lista fazemos da seguinte maneira:
```c#
List<int> inteiros = new List<int>();
```
- Na declaração segue a estrutura: `List<tipoDeDado> nomeVariavel = new List<tipoDeDado>();`
- Para mostrar o tamanho dessa lista usamos o `Count`
```c#
Console.WriteLine(inteiros.Count);
```
- Para adicionar um elemento para a Lista, usamos o `Add`;
```c#
inteiros.Add(1);
```
- Para o `Add`, passamos o valor que vai ser adicionado na Lista.
- Para recuperar valores da lista, fazemos igual aos arrays:
```c#
inteiros[0];
```
- Para remover um elemento da Lista usamos o método `Remove`
```c#
inteiros.Remove(1);
```
- Para o `Remove`, passamos o elemento que queremos remover, e não a posição
- Se quisermos remover uma posição da Lista, usamos o método `RemoveAt`
```c#
inteiros.RemoveAt(1);
```
- Para as listas podemos usar os tipos criados por Classes.