___
- Os métodos que vimos até agora são conhecidos como métodos de instância, porque, para usa-los, precisamos de uma instância do objeto.
- Mas em alguns casos, precisamos usar métodos, mas não queremos fazer uma instância do objeto, então esses métodos deveria ser estáticos, conhecidos também como métodos da classe.
- Para criar um método estático usamos a keyword `static`, como demonstra o exemplo a seguir:
```java
static void alterarCustoEmbalagem(double custoEmbalagem) {
	Produto.custoEmbalagem = custoEmbalagem;
}
```
- E para usarmos esse método, precisamos invocar ele da seguinte maneira:
```java
public class Principal {
	public static void main(String[] args) {
		Produto.alterarCustoEmbalagem(20);
	}
}
```
- Podemos criar classes apenas com métodos estáticos, elas são conhecidas como *classes utilitárias*. 