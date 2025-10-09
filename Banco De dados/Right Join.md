___
- Segue o mesmo padrão do [[Left Join]], porém agora ele retorna todos os registros da tabela da direita, mesmo que não possua um registro correspondente na tabela da esquerda.
```sql
SELECT * FROM tabela1 RIGHT JOIN tabela2 ON tabela1.id = tabela2.id;
```