___
- Para criarmos um relacionamento de um para muitos, fazemos da seguinte maneira:
```sql
-- Relacionamento Um para muitos.
CREATE TABLE course_modules (
	id INTEGER PRIMARY KEY AUTOINCREMENT,
	name TEXT NOT NULL,
	course_id INTEGER NOT NULL,

	FOREIGN KEY (course_id) REFERENCES courses(id)
)
```
- Diferente de um relacionamento de *um para um*, não usamos o `UNIQUE`;
- Quando formos definir uma chave estrangeira, ela precisa ter o mesmo tipo da chave primária da qual vamos conectar;
- E podemos visualizar os dados usando o [[Inner Join]], da seguinte maneira:
```sql
SELECT m.id, m.name, c.name, m.course_id 
FROM course_modules AS m
INNER JOIN courses AS c ON c.id = m.course_id
```
