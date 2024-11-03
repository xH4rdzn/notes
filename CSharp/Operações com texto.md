___
- Podemos fazer diversas operações com texto.
- Uma delas é a concatenação e usamos o `+` para fazer essa operação:
```c#
string texto1 = "A primeira frase.";
string texto2 = "Segunda frase";

string paragrafo = texto1 + texto2;

// Resultado no console: A primeira frase.Segunda frase
```
- Nota-se que ele não adiciona espaços, ele apenas junta as `strings`.
- Uma particularidade das `strings` é que para usar alguns caracteres especiais como a `/` ou `\`. Temos duas maneiras de resolver esse problema.
1. Duplicando os caracteres especiais:
```c#
string caminho = "C:\\teste";

// Resultado no console = C:\teste
```
2. Usando um `@`, como um prefixo da `string`
```C#
string caminho = @"C:\teste\igor\outrapasta";
```
#### `String interpolation` 
- Para usar o `string interpolation`, usamos um `$`, como prefixo de uma `string`. E podemos passar valores de variáveis para ela. Como no exemplo a seguir:
```c#
string paragrafo2 = $"A primeira frase. {texto2}";
```
#### `String builder`
- É uma classe do C#, para caso de muita concatenação de `strings`.
- Para fazer seu uso, fazemos da seguinte maneira:
```c#
using System.Text;

StringBuilder stringBuilder = new StringBuilder();
```
- E para adicionar as `strings` no `String Builder`, usamos o método `Append`.
```C#
using System.Text;

StringBuilder stringBuilder = new StringBuilder();

stringBuilder.Append(texto1);
stringBuilder.Append(texto2);
```
- E para gerar ela em apenas uma `string`, usamos o método `ToString`:
```c#
using System.Text;

string resultado = stringBuilder.ToString();
```
- Só usamos o `String Builder`, quando imaginarmos um cenário no qual perdemos o controle de concatenações de `strings`;
#### Inserindo parâmetros em `strings`
- Podemos também fazer com que as `strings` receba parâmetros, para isso usamos o método `Format`. Como no exemplo abaixo:
```C#
string texto = "O usuário {0} gosta de {1}"

string resultado = string.Format(texto, "Igor", "Java");
```
- Onde está `{0}, {1}`, será substituído pelos parâmetros que passamos no `Format`
- Podemos ter quantos parâmetros precisarmos, só precisamos lembrar que começa do 0.