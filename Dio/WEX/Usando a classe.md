___
- Quando *instanciamos* a nossa classe **Pessoa**, demos um nome para a variável que vai guardar aquela instância.
```c#
using _01_fundamentos.models

Pessoa pessoa1 = new Pessoa();

// Se usamos o pessoa1, podemos setar o nome como no exemplo abaixo:
pessoa1.Nome = "Igor";
pessoa1.Idade = 26;

// E para usarmos métodos
pessoa1.Apresentar();
```
