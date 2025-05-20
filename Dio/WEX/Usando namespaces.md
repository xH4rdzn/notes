___
- Anteriormente criamos a nossa [[Criando nossa classe no código|classe]], mas ela por si só não faz nada, ela apenas representa um objeto.
- Para poder fazer o uso dessa classe em nosso programa, precisamos fazer o que chamamos de *instância*;
- Então vamos no arquivo `Program.cs` e vamos fazer como no exemplo abaixo:
```C#
Pessoa p = new Pessoa();
```
- Porém vai dar erro, então precisamos declarar o *namespace*, então alteramos o código para o seguinte:
```c#
using _01_fundamentos.models

Pessoa p = new Pessoa();
```
- Em outras palavras o *namespace* é o caminho lógico para onde está a nossa classe;