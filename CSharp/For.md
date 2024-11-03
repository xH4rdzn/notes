___
- O `for` é um laço de repetição, em outras palavras, dada uma certa condição, enquanto essa condição for falsa, ela vai se repetir, até que a condição se torne verdadeira, assim será encerrado o nosso looping.
- Para declarar um laço `for` em C#, fazemos da seguinte maneira:
```c#
for (int i = 0; i < 10; i++) 
{
	
}
```
- Podemos usar o for, para iterar em uma Lista, como no exemplo abaixo:
```c#
class Program 
{
	static void Main() 
	{
		var lista = new List<string> {"Igor", "Lucas", "Luan"};

		for (int i = 0; i < lista.Count; i++) 
		{
			Console.WriteLine(lista[i]);
		}
	}
}
```
- Podemos aumentar a quantidade que incrementamos em `i`, em outras palavras aumentamos o nosso `step`. No exemplo abaixo vamos aumentar o passo para 2:
```c#
for (int i = 0; i < 10; i = i + 2) 
{
	
}
```