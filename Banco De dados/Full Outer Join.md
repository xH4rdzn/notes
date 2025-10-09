___
- O *Full Outer Join* é quando queremos unir duas tabelas, independente da relação entre elas.
- Onde não há correspondência é inserido o valor *null*
- Todos os registros são retornados.
```sql
SELECT * FROM tabela1 FULL OUTER JOIN tabela2 ON tabela1.id = tabela2.id;
```