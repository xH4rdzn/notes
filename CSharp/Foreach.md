___
- Usamos o `foreach`, para iterar em listas, podemos usar o `for`, porém o `foreach`, e especifico para iterar em coleções.
- Para declarar um laço `foreach`, fazemos da seguinte maneira:
```c#
class Program 
{
	static void Main() 
	{
		var lista = new List<string> {"Igor", "Lucas", "Luan"};

		foreach(var nome in lista) 
		{
			Console.WriteLine(nome);
		}

	}
}
```
- Podemos usar o `foreach`, para iterar em dicionários, como no exemplo a seguir:
```c#
class Program 
{
	static void Main() 
	{
		var dicionario = new Dictionary<string, string>();

		dicionario.Add("Nome1", "Igor");
		dicionario.Add("Nome2", "Lucas");
		dicionario.Add("Nome3", "Luan");

		foreach(var item in dicionario) 
		{
			Console.WriteLine(item);
		}

	}
}
```
- Caso queiramos iterar apenas sobre as chaves, usamos da seguinte maneira:
```c#
class Program 
{
	static void Main() 
	{
		var dicionario = new Dictionary<string, string>();

		dicionario.Add("Nome1", "Igor");
		dicionario.Add("Nome2", "Lucas");
		dicionario.Add("Nome3", "Luan");

		foreach(var item in dicionario) 
		{
			Console.WriteLine(item.Key);
		}

	}
}
```
- Se quisermos apenas o valor de cada chave, usamos da seguinte maneira:
```c#
class Program 
{
	static void Main() 
	{
		var dicionario = new Dictionary<string, string>();

		dicionario.Add("Nome1", "Igor");
		dicionario.Add("Nome2", "Lucas");
		dicionario.Add("Nome3", "Luan");

		foreach(var item in dicionario) 
		{
			Console.WriteLine(item.Value);
		}

	}
}
```