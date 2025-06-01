___
- Um objeto é uma instância de uma classe;
- Em termos simples, um objeto é uma entidade que possui estado (atributos) e comportamentos (métodos);
- *Estado*: Representado pelos atributos (variáveis do objeto).
- *Comportamento*: Representado pelos métodos (funções) do objeto.

#### Exemplo
- Quando você constrói uma casa, não começa a casa de qualquer maneira, colocando tijolos em qualquer lugar, você faz uma *planta* para decidir *metragem da casa*, o *material utilizado*, *quantos quartos*, *quantos banheiros*, etc.
- A nossa **classe** é a **planta dessa casa**, que define *todos os atributos, variáveis da nossa casa*. Na classe podemos ter comportamentos, métodos, como por exemplo, *construir* (uma função).
- O objeto vai ser a nossa casa, construída com base nessa planta.
```java
public class PlantaCasa {
	// Atributos
	int metragem;
	int numeroQuartos;
	int numeroBanheiros;
	String cor;
	String material;
}
```
- Para determinamos um método, fazemos como no exemplo a seguir:
```java
public class PlantaCasa {
	// Atributos
	int metragem;
	int numeroQuartos;
	int numeroBanheiros;
	String cor;
	String material;

	// Métodos
	public void construir() {
		System.out.println("Metragem: " + metragem);
		System.out.println("Número de Quartos: " + numeroQuartos);
		System.out.println("Número de Banheiros: " + numeroBanheiros);
		System.out.println("Material: " + material);
	}

	public void pintar() {
		System.out.println("Cor: " + cor);
	}
}
```
- Para poder instanciar um objeto fazemos da seguinte maneira:
```java
public class Casa {
	public static void main(String[] args) {
		PlantaCasa casa = new PlantaCasa();
	}
}
```
*Nota-se que passamos o nome da classe (`PlantaCasa`) como o tipo e criamos uma nova instancia dessa classe, usando a keyword `new`*;
- Para definir os valores dos atributos dessa classe, podemos fazer da seguinte maneira:
```java
public class Casa {
	public static void main(String[] args) {
		PlantaCasa casa = new PlantaCasa();


		casa.numeroBanheiros = 2;
		casa.numeroQuartos = 3;
		casa.metragem = 70;
		casa.material = "Tijolo";
		casa.cor = "cinza";
	}
}
```
- Para podermos usar os métodos definidos usamos da seguinte maneira:
```java
public class Casa {
	public static void main(String[] args) {
		PlantaCasa casa = new PlantaCasa();


		casa.numeroBanheiros = 2;
		casa.numeroQuartos = 3;
		casa.metragem = 70;
		casa.material = "Tijolo";
		casa.cor = "cinza";

		casa.construir();
		casa.pintar();
	}
}
```
*Nota-se que chamamos os métodos pelo que definimos na classe*;
