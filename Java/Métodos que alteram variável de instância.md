___
- Os métodos declarados em uma classe, podem alterar as variáveis de suas próprias instâncias dependendo da necessidade.
```java
public class Aeronave {
	boolean ativo = true;
	int totalAssentos;
	int assentosReservados;

	int calcularAssentosDisponiveis() {
		return totalAssentos - assentosReservados;
	}

	boolean desativar() {
		ativo = false;
	}
}
```
- O método `desativar`, altera a variável de instância `ativo`, diretamente de sua instância. 