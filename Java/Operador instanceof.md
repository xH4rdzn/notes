___
- Podemos usar o operador ***`instanceof`***, para podermos verificar se um objeto é de um tipo especifico;
- Podemos usar para fazer validações em métodos do quais utilizamos [[Entendendo o polimorfismo|polimorfismo]];
```java
if(conta instanceof ContaInvestimento) {
	ContaInvestimento contaInvestimento = (ContaInvestimento) conta;
	
	// Implementação
}
```
- Usando o ***`instanceof`***, temos segurança para poder fazer o *casting* para um tipo mais específico de classe;
```java
// CASTING
ContaInvestimento contaInvestimento = (ContaInvestimento) conta;
```
- Devemos evitar de utilizar o ***`instanceof`***;
