___
- Como vimos anteriormente podemos [[Criando arrays de objetos|criar um array de objetos]];
```Java
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
- E podemos também percorrer esse array, usando um laço de repetição, como no exemplo abaixo:
```java
for (int i = 0; i < turmaB.alunos.length; i++) {
	System.out.printf("%d - %s (%d anos)%n", i, turmaB.alunos[i].nome, turmaB.alunos[i].idade)
}
```
- Para ignorar um elemento que possa ser `null`,podemos fazer uma verificação
```java
for (int i = 0; i < turmaB.alunos.length; i++) {
	if(turmaB.alunos[i] != null) {
		System.out.printf("%d - %s (%d anos)%n",i, turmaB.alunos[i].nome. turmaB.alunos[i].idade);
	} else {
		SYstem.out.printf("%d - vago%n", i);
	}
}
```
- Também podemos dar uma melhorada criando uma variável para encurtar o código escrito, deixando o nosso código da seguinte maneira:
```java
for (int i = 0; i < turmaB.alunos.length; i++) {
	Aluno aluno = turmaB.alunos[i]
	if(turmaB.alunos[i] != null) {
		System.out.printf("%d - %s (%d anos)%n",i, aluno.nome. aluno.idade);
	} else {
		SYstem.out.printf("%d - vago%n", i);
	}
}
```
- Também podemos usar o outro laço `enhanced for`, como no exemplo:
```java
for(Aluno aluno : alunos) {
	if (aluno != null) {
		System.out.printf("%s (%d anos)%n", aluno.nome, aluno.idade);
	} else {
		System.out.println("vago");
	}
}
```

