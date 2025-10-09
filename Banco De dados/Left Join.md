___
- Funciona de maneira parecida com o [[Inner Join]], porém retorna todos os registros da tabela de referência (tabela da esquerda), mesmo que ele não possua um registro correspondente na tabela secundária (tabela da direita).
- Quando não é encontrado um valor correspondente na tabela secundária, é retornado ***null***
```sql
SELECT * FROM tabela1 LEFT JOIN tabela2 ON tabela1.id = tabela2.id;
```