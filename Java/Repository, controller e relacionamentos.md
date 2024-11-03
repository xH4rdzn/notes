___
### Criando a camada entity
- Para criar a camada `Entity`, precisamos criar um pacote, esse procedimento varia de `IDE` para `IDE`.
- No caso do VSCode, criamos esse pacote criando uma pasta com o nome `Entity` dentro da ultima pasta, que normalmente possui o nome do `ArtifactID` do projeto;

### Criando a camada repository
- Para criar a camada `repository`, precisamos criar um pacote, esse procedimento varia de `IDE` para `IDE`;
- Criamos da mesma maneira que a camada `Entity`

### Criando a camada Controller
- Para criar a camada `controller`, precisamos criar um pacote, esse procedimento varia de `IDE` para `IDE`;
- Criamos da mesma maneira que a camada `Entity`

### Relacionamentos Complexos
- Um relacionamento mais complexo do que os já vistos [[Relacionamento entre Entidades|anteriormente]] é o `Many-To-Many`;
- A complexidade, aqui se dá pelas diferentes características possíveis num relacionamento `Many-To-Many`, como a existência de atributos adicionais na Entidade de relacionamento, por exemplo;
- Para esse tipo de relacionamento normalmente, temos necessidade de criar uma terceira tabela, chamamos de tabela de ligação, essa tabela pode ter apenas as chaves para fazer o relacionamento, mas também podem ter atributos específicos;
- O relacionamento `Many-To-Many` é caracterizado pelas relações onde vários registros podem se relacionar com vários registros de outra tabela, e vice-versa;
- A tabela de ligação pode ter atributos próprios;
- A tabela de ligação pode ter uma chave primária única e receber como chave estrangeiras as chaves que usaremos para fazer os relacionamentos;
- Há diferentes formas de se codificar, no `Spring`, um relacionamento do tipo `Many-To-Many`, isso porque, há diferentes formas de se implementar a *tabela de ligação*.
- Para criar uma relacionamento `Many-To-Many`, usando o `Spring`, fazemos da seguinte maneira:
```java
@Entity
class CourseRegistration {

	@Id
	Long id;

	@ManyToOne
	@JoinColumn(name = "student_id")
	Student student;

	@ManyToOne
	@JoinColumn(name = "course_id")
	Course course;

	LocalDateTime registeredAt;

	int grade;

}

// Entidade Estudante

class Student {

	// ...

	@OneToMany(mappedBy = "student")
	Set<CourseRegistration> registrations;

	// ...
}


// Entidade Curso

class Course {

	// ...

	@OneToMany(mappedBy = "course")
	Set<CourseRegistration> registrations;

	// ...

}
```

