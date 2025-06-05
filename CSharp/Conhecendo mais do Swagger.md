___
- Toda vez que iniciamos a nossa aplicação, ele abre uma página do ***Swagger***, que basicamente é a documentação da nossa *api*;
- Para podermos passar para ele qual o tipo de reposta o nosso *endpoint* vai ter podemos usar o `ProducesResponseType`, como demostrado no exemplo abaixo:
```c#
[HttpGet]
[ProducesResponseType(StatusCodes.Status204NoContent)]
public IActionResult Get()
{
	// Código
}

// Devolvendo um objeto
[HttpGet]
[ProducesResponseType(typeof(NomeDaClasse), StatusCodes.Status200OK)]
public IActionResult Get()
{
	// Código
}
```
- Podemos ter mais de uma reposta possível para um *endpoint*, para documentar isso no ***Swagger***, basta duplicarmos os `ProducesResponseType`e modificando para o tipo de resposta que desejamos.
```C#

[HttpGet]
[ProducesResponseType(typeof(NomeDaClasse), StatusCodes.Status200OK)]
[ProducesResponseType(typeof(string), StatusCodes.Status200OK)]
public IActionResult Get()
{
	// Código
}
```