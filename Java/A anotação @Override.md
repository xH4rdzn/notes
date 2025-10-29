___
- A anotação ***`@Override`***,  usamos para fazer a sobrescrita de métodos;
- Quando usamos essa anotação, o compilador checa se o método está realmente sendo sobrescrito
```java
@Override
public void imprimirMensagem() {
	System.out.println("Mensagem...!");
}
```
- É uma boa ação utilizar essa anotação para sobrescrever métodos herdados;