___
- Usamos o `switch`, para poder executar um código, para cada resultado de uma variável passada para ele.
- E usamos o switch da seguinte maneira:
```c#
class Program 
{
	static void Main()
	{
		int numero = 2;

		switch(numero)
		{
			case 1:
				{
					Console.WriteLine("Caso 1");
				}
				break;
			case 2:
				{
					Console.WriteLine("Caso 2");
				}
				break;
		}

	}
}
```
- Se quisermos executar algum comportamento, caso não seja nenhuma das opções, usamos o `default`:
```c#
class Program 
{
	static void Main()
	{
		int numero = 2;

		switch(numero)
		{
			case 1:
				{
					Console.WriteLine("Caso 1");
				}
				break;
			case 2:
				{
					Console.WriteLine("Caso 2");
				}
				break;
			default:
				{
					Console.WriteLine("Caso Padrão");
				}
				break;
		}

	}
}
```
- Fazendo o `switch` com números, podemos comparações também da seguinte maneira:
```c#
class Program 
{
	static void Main()
	{
		int numero = 2;

		switch(numero)
		{
			case < 1:
				{
					Console.WriteLine("Caso 1");
				}
				break;
			case >= 2:
				{
					Console.WriteLine("Caso 2");
				}
				break;
			default:
				{
					Console.WriteLine("Caso Padrão");
				}
				break;
		}

	}
}
```
- Temos uma maneira mais curta de fazer um `switch`, como mostrado no exemplo a seguir:
```c#
class Program 
{
	static void Main()
	{
		int numero = 7;
		string resultado = numero switch
		{
			7 => "Igor",
			1 => "Luan",
			3 => "Lucas",
			_ => "Nome Desconhecido"
		};

	}
}
```