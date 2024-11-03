___
- Podemos usar o `return`, também para encerrar o looping.
- A unica diferença é que, o `return`, podemos usar dentro de funções, ou de `if`, como no exemplo a seguir:
```c#
void Teste(int numero)
{
	if (numero == 5)
		return;

	Console.WriteLine("valor qualquer"); // Não sera executado caso o numero seja 5
}
```