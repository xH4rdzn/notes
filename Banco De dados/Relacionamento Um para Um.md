___
- Para fazer um relacionamento de 1:1, precisamos chamar uma chave estrangeira;
- Para fazer isso fazemos seguindo o exemplo abaixo:
```sql
CREATE TABLE student_adress (
	id INTEGER PRIMARY KEY AUTOINCREMENT,
  student_id INTEGER UNIQUE NOT NULL,
  street TEXT NOT NULL,
  city TEXT NOT NULL,
  
  -- Conectando com outra tabela, em um relacionamento 1:1
  FOREIGN KEY (student_id) REFERENCES students(id)
)
```
- `UNIQUE` -> Dado único;
- `FOREIGN KEY` -> Chave estrangeira, dizemos ao banco a qual coluna que vamos conectar a outra coluna de outra tabela;
- `REFERENCES`-> Indicamos a qual tabela e campo dessa outra tabela vamos conectar o campo passado antes desse comando;