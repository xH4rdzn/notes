___
- Ao criamos um projeto de api, uma pasta chamada `Controllers` irá ser criada juntamente com a estrutura do projeto.
- Dentro dessa pasta vamos por classes do tipo `controller`;
- Os ***controllers*** são funções que se tornam os *endpoints* em nossa api, que executam uma função especifica;
- Servem para fazer agrupamento de funções para um *endpoint* especifico;
- Para criar um controller na raiz do nosso projeto vamos criar uma pasta com o nome `Controllers`, e dentro dessa pasta vamos criar os arquivos que desejamos que sejam um controller. Como por exemplo o `UserController`, nesse caso iriamos criar o arquivo `UserController.cs`e dentro desse arquivo faríamos o seguinte:
```c#
namespace MinhaPrimeiraApi.Controllers;

[Route("[controller]")]
[ApiController]

public class UserController: COntrollerBase
{
	// Código
}
```