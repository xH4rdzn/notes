___
- Quando uma `exception` é lançada todas as linhas abaixo de onde ocorreu o erro não são executadas.
- Mas para podermos manter o fluxo, para que o nosso programa não pare a execução usamos o bloco `try-catch`:
```java
try {
	int resultado = 5 / 0;
	System.out.println("O resultado da divisão é: " + resultado);
} catch (ArithmeticException e) {
	System.out.println("O motivo do erro foi: " + ex.getMessage())
}
```