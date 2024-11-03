___
- Para declarar uma função que retorna algum valor, seguimos a ordem abaixo para poder retornar um valor:
- `modificadorDeAcesso tipoDeRetorno NomeFuncao(parâmetros){}`
- Como exemplo, vamos modificar a função `Adicionar`, que criamos [[Funções com Parâmetros||anteriormente]]
```C#
public int Adicionar(int valor1, int valor2) {
	var resultado = valor1 + valor2;

	return resultado;
}
```
- Para devolver um valor ou algo de uma função usamos a keyword `return`, só precisamos nos atentar ao tipo de dado que vamos retornar
- Não precisamos armazenar o valor a ser retornado em uma variável, podemos simplesmente só retornar o valor, como no exemplo abaixo:
```c#
public int Adicionar(int valor1, int valor2) {
	return valor1 + valor2;
}
```
- Como nossa função tem apenas uma linha, podemos escrever a nossa função da seguinte maneira
```c#
public int Adicionar(int valor1, int valor2) => valor1 + valor2;
```
- A função acima irá funcionar da mesma maneira, que das maneiras anteriores, só precisamos nos atentar que funções assim só podem ter uma linha de código.
- Podemos também retornar mais de um valor em uma função, para fazer com que a função retorne mais de um valor seguimos o exemplo abaixo:
```c#
public (int, string) Adicionar(int valor1, int valor2) 
{
	valor resultado = valor1 + valor2;

	return (resultado, "igor");
}
```
- Agora temos dois retornos diferentes, e para usar esses retornos de maneiras isoladas fazemos da seguinte maneira:
```c#
class Program 
{
	static void Main()
	{
		var matematica = new OperacoesMatematicas();

		var soma = matematica.Adicionar(1, 7);
		Console.WriteLine(soma.Item1);
		Console.WriteLine(soma.Item2);

	}
}
```
- Ainda, existe a possibilidade de nomear esses retornos, e para fazer isso seguimos o exemplo abaixo:
```c#
public (int resultadoDaAdicao, string autor) Adicionar(int valor1, int valor2)
{
	var resultado = valor1 + valor2;

	return (resultado, "Igor");
}
```
- E agora, no lugar de usarmos `Item1` ou `Item2`, usamos da seguinte maneira:
```c#
class Program 
{
	static void Main()
	{
		var matematica = new OperacoesMatematicas();

		var soma = matematica.Adicionar(1, 7);
		Console.WriteLine(soma.resultadoDaAdicao);
		Console.WriteLine(soma.autor);

	}
}
```
- E onde vamos usar essa função, também podemos fazer da seguinte maneira:
```c#
(int resultado, string nome) = matematica.Adicionar(7,3);
Console.WriteLine(resultado);
Console.WriteLine(autor);
```