___
- Os modificadores são conhecidos também como modificadores de visibilidade, esses modificadores permitem controlar o acesso de classes, atributos, métodos e construtores.
- Existem 4 tipos de modificadores;

#### Default
- É quando não definimos nenhum modificador de acesso, como demostrado no exemplo abaixo:
```java
class Pedido {
	
	// Código
}
```
- O modificador ***default***, deixa a classe, atributos, métodos entre outros, visível apenas no ***package*** em que ela se encontra.

#### Public
- É quando usamos a *keyword* ***public***, como demonstrado no exemplo abaixo:
```java
public class Pedido {
	
	// Código
}
```
- Esse modificador, torna qualquer elemento de uma classe acessível para todos os pacotes e partes da nossa aplicação;