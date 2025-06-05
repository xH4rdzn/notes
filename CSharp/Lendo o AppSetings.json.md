___
- Para lermos as propriedades do arquivo `Appsettings.json`, vamos no arquivo `Program.cs`, pois nele temos acesso aos `builder`.
- E fazemos como no exemplo:
```json
// Declarando uma propriedade no arquivo appsettings.json

{
	"Prop1": "Igor"
}
```
- E para ler essa propriedade no arquivo `Program.cs`:
```c#
builder.Configuration.GetSection("Prop1").value;
```
- Desta maneira ele devolve o valor da nossa propriedade;
- Podemos fazer isso de maneira encadeada, no caso de objetos. Para isso podemos fazer da seguinte maneira:
```c#
builder.Configuration.GetSection("Loggin").GetSection("login").value;
```
- Se tivermos duas propriedades iguais nos arquivos, ele vai dar ***preferência para o nosso ambiente***;
- Podemos também fazer por meio de classes, *porém as propriedades da classe precisam ter o mesmo nome* das propriedades do `Appsettings.json`, e a recuperamos seus valores da seguinte maneira:
```c#
public class MyClass 
{
	public string Prop1 { get; set; }

	public string Prop2 { get; set; }

	public string PropA { get; set; }
}

// E para recuperarmos ela em Program.cs
builder.Configuration.GetSection("MyClass").Get<MyClass>();
```
- Se tentarmos recuperar uma propriedade que não foi definida seu valor será `null`;
- O `Value`, sempre vai devolver o valor em formato de ***string***;
- Uma maneira simplificada de recuperar esses valores é da seguinte forma:
```c#
builder.Configuration.GetValue<int>("MyClass:Number");
```