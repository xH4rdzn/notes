___
- Constantes são variáveis que não podem alterar o seu valor
- Para declarar uma constante usamos a keyword `final` e declaramos ela da seguinte maneira:
```java
public class Visitante {

	static final int IDADE_MINIMA_ACESSO_IRRESTRITO = 18;

}
```
- Em java, as constantes, por convenção, é escrita toda em maiúsculo.
- Usamos o `static`, para deixar ela como uma variável de classe.
- E para usarmos essa variável, fazemos da seguinte maneira:
```java
Visitante.IDADE_MINIMA_ACESSO_IRRESTRITO;
```