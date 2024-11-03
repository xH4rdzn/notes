___
- Para fazer a composição de objetos, colocamos como um `atributo`.
- Composição é um objeto que se relaciona com outro objeto.
- Por exemplo, um objeto do tipo `Carro`, tem relação com um objeto do tipo `Pessoa`. E para fazer esse relacionamento seguimos o exemplo abaixo:
```java
public class Carro {
	String fabricante;
	String modelo;
	String cor;
	int anoFabricacao;
	Pessoa proprietario;
}
```
- Podemos ler que: *todo carro possui um proprietário*;
- Agora precisamos atribuir um objeto do tipo `Pessoa`, a seguir [[Atribuindo o objeto da composição|nesta nota]].