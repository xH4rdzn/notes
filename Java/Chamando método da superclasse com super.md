___
- Mesmo quando sobrescrevemos um método, podemos chamar o método '*original*' no qual sobrescrevemos;
- Para fazer isso usamos a *keyword* ***`super`***, assim ela vai chamar o método que está na super classe;
```java
@Override
public void imprimirDemonstrativo() {
	super.imprimirDemonstrativo();
	System.out.printf("Saldo Disponível: %.2f%n", getSaldoDisponivel());
}
```