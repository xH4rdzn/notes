___
- Uma subquery ou subconsulta, é uma instrução SQL dentro de outra instrução SQL, ou seja, é basicamente uma consulta embutida dentro de outra consulta.
- Dessa forma, ela funciona passando os resultados da consulta mais interna para a consulta mais externa através de uma condição.
- Além disso, também é possível utilizar subconsulta em operações como INSERT, UPDATE, DELETE.
```sql
SELECT
	coluna1,
	...,
	colunaN
FROM nome_da_tabela WHERE condição (
	SELECT coluna FROM nome_da_tabela [WHERE condiçao]
);
```