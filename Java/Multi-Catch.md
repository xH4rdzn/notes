___
- Podemos capturar mais de uma `exception`, como no exemplo abaixo:
```java
public class TesteExceptions {
	public static void main(String[] args) {
		try {
			int resultado = 10 / 2;
			System.out.println("O resultado da divisão é: " + resultado);
			Conta conta = null;
			conta.depositar(1000);
		} catch(ArithmeticException e) {
			System.out.println("O motivo do error foi: " + e.getMessage());
		} catch(NullPointerException e) {
			System.out.println("A classe conta não foi instanciada. O motivo foi: " + e.getMessage());	
		}
		
	}
}
```
- Podemos usar quantos `catch`, precisarmos;
- **Chamamos isso de `multi-catch`**;
- Podemos também fazer da seguinte maneira:
```java
catch(ArithmeticException | NullPointerException e) {
	System.out.println("O motivo do erro foi : " + e.getMessage());
}
```
