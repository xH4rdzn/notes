___
- Caso queiramos, verificar se algo é verdadeiro e executar um bloco de código, ou caso ele seja falso executarmos outro bloco de código usamos a palavra reservada `if`.
- Como no exemplo abaixo, vamos verificar se a variável `numero` é positiva:
```C#
public class Program
{
	static void Main()
	{
		int numero = -10;

		if (numero > 0) 
		{
			Console.WriteLine("Este número é positivo")
		}
	}
}
```
- Temos algum operadores para poder fazer essas comparações lógicas e são:
	- > -> maior que;
	- < -> menor que;
	- == -> igual a;
	- <= -> menor ou igual a;
	- >= -> maior ou igual a;
	- != -> Diferente de;
- Caso a condição passada para o `if`, for falsa, usamos o `else`. Seguindo o exemplo:
```c#
public class Program
{
	static void Main()
	{
		int numero = -10;

		if (numero > 0) 
		{
			Console.WriteLine("Este número é positivo");
		}
		else 
		{
			Console.WriteLine("Este número é negativo");
		}
	}
}
```
- Caso tenhamos mais de uma condição a ser atendida, usamos o `else if`. Seguindo como no exemplo abaixo:
```c#
public class Program
{
	static void Main()
	{
		int numero = -10;

		if (numero > 0) 
		{
			Console.WriteLine("Este número é positivo");
		}
		else if (numero == 0)
		{
			Console.WriteLine("Este número é NEUTRO");
		}
		else 
		{
			Console.WriteLine("Este número é negativo");
		}
	}
}
```
- Podemos ter quantos `else if`, precisarmos no código.
- No caso de condições que recebe valores booleanos, podemos passar apenas o nome da variável para o `if`. Como no exemplo a seguir:
```c#
public class Program
{
	static void Main()
	{
		bool ativo = true;

		if (ativo) 
		{
			Console.WriteLine("Entrou");
		}
		
	}
}
```
- Caso queiramos verificar se o valor é falso, precisamos apenas inverter o valor booleano, neste caso usamos o `!`. Como no exemplo a seguir:
```c#
public class Program
{
	static void Main()
	{
		bool ativo = true;

		if (!ativo) 
		{
			Console.WriteLine("Entrou");
		}
		
	}
}
```
- Para `strings`, usamos o método `Equals()`, e como parâmetro dessa função passamos com o que queremos comparar. Como no exemplo a seguir:
```c#
ublic class Program
{
	static void Main()
	{
		string autor = "Igor";

		if (autor.Equals("Igor")) 
		{
			Console.WriteLine("É igual");
		}
		
	}
}
```
- Caso queiramos ver se é diferente, para `strings`, basta invertemos o resultado usando o `!`:
```c#
public class Program
{
	static void Main()
	{
		string autor = "Igor";

		if (!autor.Equals()) 
		{
			Console.WriteLine("É diferente");
		}
		
	}
}
```
- Podemos usar outros operadores para poder comparar, chamamos eles de operadores lógicos e são:
	- `&&` -> Operador lógico E, só da `true`, caso as duas comparações forem verdadeiras
	- `||` -> Operador OU, da `true`, quando pelo menos uma das comparações forem verdadeiras.
```c#
public class Program
{
	static void Main()
	{
		bool ativo = true;
		int numero = 10

		// Usando operador &&
		if (numero > 0 && ativo) 
		{
			Console.WriteLine("Os dois são verdadeiro");
		}
		
	}
}
```
- Podemos verificar também se um valor é `null`. Para fazer isso seguimos o exemplo abaixo:
```c#
public class Program
{
	static void Main()
	{
		string mensagemDeErro = null;

		
		if (mensagemDeErro is null) 
		{
			Console.WriteLine("É nulo");
		}
		
	}
}
```
- Temos a operação inversa também, caso queiramos executar um código caso não seja nulo:
```c#
public class Program
{
	static void Main()
	{
		string mensagemDeErro = null;

		
		if (mensagemDeErro is not null) 
		{
			Console.WriteLine("Não é nulo");
		}
		
	}
}
```
- Podemos fazer várias comparações lógicas na mesma condição:
```c#
public class Program
{
	static void Main()
	{
		int numero = 10;
		double saldo = 100.00;
		bool ativo = true;
		
		if ((numero == 0 && saldo >= 100)|| ativo) 
		{
			Console.WriteLine("Entrou aqui");
		}
		
	}
}
```
- Só precisamos separar com `()`, para não acabar tendo um resultado que não é esperado.
- Temos outra maneira de fazer `if` , que é uma forma mais reduzida, e chamamos de [[Condicional Ternário||operador ternário]].