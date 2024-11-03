___
- É uma forma de organizar as nossas classes, interfaces e arquivos dentro de um projeto C#.
- Criamos um namespace da seguinte maneira:
```C#
namespace nome
```
- Existe um padrão de nomenclatura para os namespace.
- Sempre o primeiro nome é o nome do projeto.
```C#
namespace HelloWorld;
```
- Se dentro desse projeto existir mais pastas, ai fazemos uma concatenação entre o nome do Projeto e o nome da pasta.
```C#
namespace HelloWorld.pastaUm;
```
- Se existir outra pasta dentro da pasta seguimos o exemplo abaixo:
```C#
namespace HelloWorld.pastaUm.pastaUmDois;
```
- Em versões mais antigas, precisamos declarar o namespace da seguinte maneira:
```C#
namespace HelloWorld {}
```
- Mas em versões mais novas, usamos o `;`:
```C#
namespace HelloWorld;
```
