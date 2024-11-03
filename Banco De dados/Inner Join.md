___
- Quando temos uma tabela com um relacionamento com uma outra tabela ou outras tabelas, sempre vamos ter uma chave estrangeira, que é uma coluna de conexão.
- O comando `INNER JOIN`, retorna os registros onde existe uma correspondência em ambas as tabelas.
```sql
SELECT a.id, a.student_id, a.street, a.city, s.name
FROM student_adress AS a
INNER JOIN students AS s ON s.id = a.student_id
```
- `ON` -> Serve para definir qual coluna, vamos usar para fazer essa conexão;
- Usamos os nomes renomeados para retornar os dados, caso contrário pode dar erro de ambiguidade;