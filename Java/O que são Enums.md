___

### O que são Enums ?
- **Enums**, ou *Enumerations*, são um tipo especial de classe que permite representar um conjunto fixo de constantes.
- Eles são úteis para lidar com valores que não mudam, como dias da semana, estados de um sistema, ou tipos de acesso.

### Como criar um Enum dentro do Java?
- Para podermos criar um Enum, dentro do *java*, podemos fazer como no exemplo abaixo:
```java
public enum NomeDoEnum {
	
	// Valores fixos
	ADMIN("Administrador do Sistema"),
	USUARIO("Usuário do Sistema"),
	CONVIDADO("Convidado do Sistema");
	
	// Atributos
	private String descricao;
	
	// Método Construtor
	NomeDoEnum(String descricao) {
		this.descricao = descricao;
	}
	
	// Métodos
	public String getDescricao() {
		return this.descricao;
	}
}
```