___
- Para criar funções/métodos, fazemos a declaração seguindo:
- `modificadorDeAcesso tipoDeRetorno NomeFunção(parâmetros) {}`
- Como no exemplo abaixo que vamos criar a função `Adicionar`, que recebe dois valores como parâmetros:
```c#
public void Adicionar(int valor1, int valor2) {}
```
- Como percebemos os parâmetros precisam ter seu tipo definido, como no exemplo acima que recebemos dois parâmetros do tipo `int`
- Dentro do escopo dessa função podemos usar os parâmetros como se fossem variáveis:
```c#
public void Adicionar(int valor1, int valor2) {
	var resultado = valor1 + valor2;

	Console.WriteLine(resultado);
}
```
- Em C#, podemos passar parâmetros de forma nomeada, para fazermos isso, seguimos o exemplo abaixo:
```c#
class Program 
{
	static void Main()
	{
		var matematica = new OperacoesMatematicas();

		matematica.Adicionar(valor1: 1, valor2: 7);
	}
}
```
- O código acima é a mesma coisa que:
```c#
class Program 
{
	static void Main()
	{
		var matematica = new OperacoesMatematicas();

		matematica.Adicionar(1, 7);
	}
}
```
- É a mesma coisa, porém, com os parâmetros nomeados ficam mais fácil de entender, além de que a ordem não importa quando passamos os parâmetros de maneira nomeada.