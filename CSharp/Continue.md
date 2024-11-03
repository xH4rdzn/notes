___
- Usamos essa keyword, para pular um determinado valor do looping, mas não queremos encerrar o looping;
- Vemos um exemplo abaixo:
```c#
while (numero < 10)
{
	numero++

	if (numero == 5)
	{
		continue;
	}

	Console.WriteLine(numero);
}
```