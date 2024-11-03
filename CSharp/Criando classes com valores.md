___
- Para criar uma classe com atributos, podemos seguir o exemplo abaixo:
```c#
public class Carro 
{
	public string Modelo { get; set;}

	public DateOnly LancadoEm { get; set;}

	public Cor Cor { get; set;}

	public void NomeDoModelo() => Console.WriteLine(Modelo);
}


// O enum deve ser feito em outro arquivo
public enum Cor 
{
	Vermelho,
	Azul,
	Amarelo
}


```
- Se instanciarmos o objeto `Carro`, e chamar a função `NomeDoModelo`, e executar esse projeto, não vai exibir nada no terminal, pois não definimos nenhum valor para o Modelo em si.
- Para atribuir um valor para essa variável existem 3 formas.
- Acessando diretamente o atributo:
```c#
public class Program
{
	static void Main() 
	{
		var carro = new Carro();
		carro.Modelo = "Ferrari";
	}
}
```
- Podemos fazer isso pois na classe definimos a variável `modelo`, como publica, então podemos acessar ela diretamente.
- Outra maneira de atribuir valores, e no momento de instanciar o objeto, como no exemplo abaixo:
```c#
public class Program
{
	static void Main() 
	{
		var carro = new Carro 
		{
			Modelo = "Ferrari",
			LancadoEm = new DateOnly(2021, 10, 25),
			Cor = Cor.Azul
		};
	}
}
```
- Se quisermos deixar uma propriedade como obrigatória, para poder fazer a instancia do objeto usamos a keyword `required`, como demonstrado no exemplo abaixo:
```c#
public class Carro 
{
	public required string Modelo { get; set;}

	public DateOnly LancadoEm { get; set;}

	public Cor Cor { get; set;}

	public void NomeDoModelo() => Console.WriteLine(Modelo);
}
```
- Se não quisermos usar o `required`, podemos criar um método construtor para o objeto, para fazer isso fazemos seguindo o exemplo:
```c#
public class Carro 
{
	public required string Modelo { get; set;}

	public DateOnly LancadoEm { get; set;}

	public Cor Cor { get; set;}

	public void NomeDoModelo() => Console.WriteLine(Modelo);

	public Carro(string modelo) 
	{
		Modelo = modelo;
	}
}
```
- O método construtor é chamado toda vez que tentamos instanciar um novo objeto.
