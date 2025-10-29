___
- O modificador de acesso ***`protected`***, ele diz que um membro da classe, pode ser acessado por subclasses, independente do pacote em que se encontra;
- Ele também permite acesso aos membros da classe, por outras classes que estejam no mesmo pacote, mesmo que não estejam utilizando herança;
```java
public class Conta {
	
	// Variáveis de instância
	protected double saldo;
	
	
	protected void setSaldo(double saldo) {
		this.saldo = saldo;
	}
}
```
- Para caso de sobrescrita de métodos, podemos fazer o que chamamos de *expandir o nível de visibilidade*, que é trocar por exemplo de ***`private`*** para ***`public`***;