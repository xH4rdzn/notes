___
- O modificador de acesso ***private***, ele torna um membro que o usamos, privado, de maneira que apenas a classe tem acesso a aquele membro.
- ***Não podemos usar o `private`em classes***, apenas em métodos, variáveis de instância e métodos;
```java
public class Produto {
	
	private final String codigo;
	private String nome;
	private int quantidadeEstoque;
	
}
```