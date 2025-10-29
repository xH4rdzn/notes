___
- Essa função é para facilitar o uso do [[Operador instanceof]];
- Para podermos utilizar esse **Pattern Matching**, fazemos como no exemplo abaixo:
```java
if (conta instanceof ContaInvestimento contaInvestimento) {
	// Verificação
}
```
- Nesse caso, se o resultado do teste lógico for *true*, ele já vai fazer o *casting* de maneira automática;
- Desta maneira podemos declarar a variável e já fazer a verificação que desejamos;
