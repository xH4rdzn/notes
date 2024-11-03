___
- A keyword `static`, é usada para associar um método a própria classe, sendo assim, para usar um método não precisamos instanciar uma classe.
- Para usar esse método podemos fazer seguindo o exemplo:
```c#
// Classe operações matemáticas
public class OperacacoesMatematicas
{
	public static int Adicionar(int valor1, int valor2) => valor1 + valor2;
}
```
- Podemos usar para atributos também, porém esta variável vai ser compartilhada com todas as instancias do objeto.
- Já em métodos, significa que não precisamos instanciar uma classe para fazer uso desse método.
- Podemos marcar uma classe como `static` também, porém todos métodos que ela possui, precisam ser `static`, também.
- ***Não é comum utilizar o static para variáveis, apenas para métodos.***
