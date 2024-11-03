___
- Para variáveis do tipo texto, temos dois grupos o grupo `char` e o grupo `string`
- O `char` é apenas um caractere e declaramos e usamos ele como no exemplo abaixo:
```c#
char letra = 'a';
```
- Podemos também passar números e caracteres especiais, desde que os mesmos estejam entre aspas e que se for usado o tipo `char` sejam apenas um caractere:
```c#
char numero = '1';
char caracter = '@';
```
- Mas normalmente queremos escrever uma frase completa, em outras palavras uma sequencia de caracteres, para isso usamos o tipo `string`:
```C#
string texto = "Este curso é muito bom";
```
- Quando usamos o tipo `string`, ele é uma lista de `char`, então temos acesso a alguns métodos ou então podemos separar da seguinte maneira:
```c#
string texto = "Este curso é muito bom";
char primeiraLetraDoTexto = texto[0];
```
- No tipo `string`, temos acesso a alguns métodos que já estão ligados ao tipo `string` como o método `Trim()` que retira os espaços da `string`:
```C#
string meuNome = "    Igor    ";
string nomeSemEspaco = meuNome.Trim();
```
- Temos outros métodos associados ao tipo `string`, como o `StartsWith`, `EndsWith`,`Replace`, por exemplo.
```C#
// Usando o Replace
string textoAposReplace = nomeSemEspaco.Replace('e', '7');
```
- Temos outras funções para o tipo texto também, podemos ver na documentação oficial.