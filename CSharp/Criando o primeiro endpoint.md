___
- Para podermos criar um endpoint, no arquivo do [[O que é um controller|controller]], criamos um método. ***Pois endpoints são métodos***
```c#
[HttpGet]
public IActionResult Get()
{
	return Ok();
}
```
- *Nota-se que todos os métodos que são endpoints, devem retornar um `IActionResult`*;
- Passamos entre `[]`, o tipo de método HTTP que esse método vai executar, no exemplo acima ele executa uma requisição do tipo `GET`;
- Para configurar as nossas rotas com todas as letras minúsculas, vamos ao arquivo `Program.cs`e adicionamos o método abaixo:
```C#
builder.Services.AddRouting(option => option.LowercaseUrls = true);
```