___
- Até o momento vimos que tudo em Java são objetos, menos os tipos primitivos
- Os tipos primitivos não aceitam atribuição do valor `null`;
- Em alguns casos, precisamos atribuir o valor `null`, e nos tipos primitivos não é possível, então usamos as classes `wrappers`. Que são:
	- `Integer` -> para inteiros;
	- `Double` -> para pontos flutuantes do tipo `double`;
	- `Long` -> para inteiros longos;
	- `Float` -> para pontos flutuantes do tipo `float`;
	- `Character` -> para o tipo `char`;
	- `Boolean` -> para o tipo `boolean`;
- E quando declaramos uma variável utilizando um `wrapper`, podemos atribuir o valor `null`;
- Para atribuirmos/criarmos uma instância de `Integer` ou de qualquer outro `wrapper`, usamos o método estático `valueOf`, assim podemos atribuir um valor para o `wrapper` que queremos usar:
```java
public class Principal {
	public static void main(String[] args) {

		// Declarando com Wrappers
		Integer diasParaEntrega;
		Long codigoEntrega;
		Float valorFrete;
		Double valorTotal;
		Character tipoCliente;
		Boolean compraPaga;

		// Atribuindo valor para um wrapper
		diasParaEntrega = Integer.valueOf(20);

	}
}
```