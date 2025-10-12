___
- Ao aplicarmos o ***encapsulamento*** precisamos criar os métodos de acesso as nossas variáveis de instância;
- Para criarmos esses métodos precisamos seguir uma convenção;
- Para métodos que vamos apenas *pegar* o valor dessa variável usamos o prefixo `get`, como demonstrado no exemplo abaixo:
```java
public class Produto {

	private String name;
	private String codigo;
	private double valor;
	
	// Getters
	public String getName() {
		return name;
	}
	
	public String getCodigo() {
		return codigo
	}
	
	public double getValor() {
		return valor;
	}

}
```
- Para variáveis do tipo ***`boolean`*** usamos o prefixo `is`, como no exemplo abaixo:
```java
public class Produto {

	private String name;
	private String codigo;
	private double valor;
	private boolean ativo;
	
	// Getters
	public String getName() {
		return name;
	}
	
	public String getCodigo() {
		return codigo
	}
	
	public double getValor() {
		return valor;
	}
	
	public boolean isAtivo() {
		return ativo;
	}

}
```
- E para métodos que fazem a alteração do valor dessas variáveis de instância usamos o prefixo ***`set`*** como no exemplo abaixo:
```java
public class Produto {

	private String name;
	private String codigo;
	private double valor;
	private boolean ativo;
	
	// Getters
	public String getName() {
		return name;
	}
	
	public String getCodigo() {
		return codigo
	}
	
	public double getValor() {
		return valor;
	}
	
	public boolean isAtivo() {
		return ativo;
	}
	
	// Setters
	public void setName(String name) {
		this.name = name;
	}
	
	public void setValor(double valor) {
		this.valor = valor;
	}

}
```
- Não precisamos criar `getters`e `setters`, para todas as nossas variáveis de instância, depende da regra de negócio da aplicação.