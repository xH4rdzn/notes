___
- Sempre que tivermos esse tipo de relacionamento, vamos precisar criar uma tabela, para guardar as informações;
- Essa tabela criada vai conectar as duas tabelas, como no exemplo abaixo que vamos criar uma tabela de estudantes e cursos que esse estudante(s) faz;
```sql
CREATE TABLE students_courses (
	id INTEGER PRIMARY KEY AUTOINCREMENT,
	student_id INTEGER NOT NULL,
	course_id INTEGER NOT NULL,

	FOREIGN KEY (student_id) REFERENCES students(id),
	FOREIGN KEY (course_id) REFERENCES courses(id)
)
```
- Normalmente essas tabelas criadas em relacionamentos muitos para muitos, ela vai ter mais colunas de chaves.
- Para inserir dados em tabelas com esse tipo de relacionamento fazemos como no exemplo abaixo:
```sql
INSERT INTO students_courses
(student_id, course_id)
 VALUES
 (id do Estudante, id do Curso) -- Lembrando que eles são inteiros.
```
- Para selecionar esses campos podemos fazer múltiplos `INNER JOIN`, como demostrando abaixo:
```sql
SELECT sc.id, sc.student_id, s.name AS student, sc.course_id, c.name AS course 
FROM students_courses AS sc
INNER JOIN students AS s ON s.id = sc.student_id
INNER JOIN courses AS c ON c.id = sc.course_id
```