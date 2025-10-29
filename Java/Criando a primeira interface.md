___
- Para criarmos uma interface em *Java*, podemos fazer da seguinte maneira:
```java
public interface nomeDaInterface {}
```
- Dentro de uma interface, definimos métodos abstratos que ao ser implementados, fazemos apenas a sua declaração;
- Para declarar métodos em uma interface podemos seguir como no exemplo abaixo:
```java
public interface DocumentoPagavel {
	
	double getValorTotal();
	
	Beneficiario getBeneficiario();
}
```
- E para podermos utilizarmos essa interface em classes, fazemos da seguinte maneira:
```java
public class Documento implements DocumentoPagavel {}
```
- Agora basta implementar os métodos que estão em nossa interface;
