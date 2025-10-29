___
- Para poder comparar a igualdade entre objetos, pelo conteúdo, devemos sobrescrever o método ***`equals`***;
- Todos os objetos possuem esse método, pois ele é herdado diretamente da classe ***`Object`***;
- Caso não sobrescrevermos esse método, ele vai comprar pela referência em memória;
- Para poder sobrescrever esse método podemos seguir como o exemplo abaixo:
```java
@Override
public boolean equals(Object obj) {
	if (this == obj) return true;
	if(obj == null) return false;
	if(this.getClass() != obj.getClass()) return false;
	Conta conta = (Conta) obj;
	if(this.agencia != conta.getAgencia()) return false;
	if(this.numero != conta.getNumero()) return false;
}
```
