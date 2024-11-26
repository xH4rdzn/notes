___
- Para utilizarmos um array de uma classe que criamos, podemos criar como no exemplo abaixo:
```java
public class Turma {

	String identificacao;
	String nomeProfessora;
	Aluno[] alunos;
}
```
*Nota-se que `Aluno`é a classe que criamos, e também não inicializamos esse array;*
- E para usarmos essa classe e esse *array* de objetos do tipo **aluno**, podemos fazer da seguinte maneira:
```java
public class Principal {
	public static void main(String[] args) {
		Turma turmaB = new Turma();
		turmaB.identificacao = "Maternal B";
		turmaB.nomeProfessora = "Tia Maria";
		// instanciando o array de alunos
		turmaB.alunos = new Aluno[3];
	}
}
```
- Mas como `aluno` é uma classe de um objetos, para usar ele precisamos fazer a instancia de um aluno, como no exemplo a seguir:
```java
public class Principal {
	public static void main(String[] args) {
		Turma turmaB = new Turma();
		turmaB.identificacao = "Maternal B";
		turmaB.nomeProfessora = "Tia Maria";
		// instanciando o array de alunos
		turmaB.alunos = new Aluno[3];
		// instanciando um aluno
		turmaB.alunos[0] = new Aluno();
		// atribuindo nome e idade para o aluno instanciado
		turmaB.alunos[0].nome = "Igor";
		turmaB.alunos[0].idade = 26;
		
	}
}
```
- Também podemos instancia de maneira separada e adicionar ao `array`, como demostra no exemplo abaixo:
```java
public class Principal {
	public static void main(String[] args) {
		Turma turmaB = new Turma();
		turmaB.identificacao = "Maternal B";
		turmaB.nomeProfessora = "Tia Maria";
		// instanciando o array de alunos
		turmaB.alunos = new Aluno[3];

		// insntanciando um aluno de maneira separada
		Aluno aluno1 = new Aluno();
		aluno1.nome = "Lucas";
		aluno1.idade = 15;

		// Vinculando a um array
		turmaB.alunos[1] = aluno1;
		
	}
}
```