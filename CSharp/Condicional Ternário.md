___
- O condicional ternário, é uma maneira mais enxuta de escrever um bloco de código do tipo `if`.
- E usamos esse condicional ternário da seguinte maneira:
```c#
class Program 
{
	static void Main() 
	{
		int numero = 7;
		string autor = numero == 7 ? "Igor" : "Luan";
	}
}
```
- Podemos por mais condições:
```c#
class Program 
{
	static void Main() 
	{
		int numero = 7;
		string autor = numero == 7 || numero > 100 ? "Igor" : "Luan";
	}
}
```