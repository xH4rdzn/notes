___
- Devemos criar uma pasta com o nome de `models`na raiz do nosso projeto.
- Criar um arquivo de classe, no qual passamos o nome;
- *Todo nome de classe deve começar com letra maiúscula**
- Para criarmos uma classe em C#, podemos seguir como no exemplo abaixo:
```C#
namespace _01_fundamentos.models
{

	public class Pessoa
	{
		public string Nome { get; set; }
		public int Idade { get; set; }

		public void Apresentar()
		{
			Console.WriteLine($"Olá, meu nome é {Nome}, e tenho {Idade} anos");
		}

	}

}
```