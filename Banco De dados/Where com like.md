___
- Diferente do [[Where com Igualdade]], que busca por exatamente igual, o `WHERE` com `LIKE`, busca por registros que tenham pelo menos uma parte do que é passado como condição.
- É usado com a `%`, como no exemplo abaixo:
```sql
-- Retorna todos os registros que na coluna name termina com 'web'
SELECT * FROM products WHERE name LIKE '%cam'
```
- Essa `%`, se colocarmos no inicio, significa que a palavra deve terminar com o que passamos para a condição.
- Se quisermos procurar por um registro que comece com a condição passamos a `%` no final da condição, como no exemplo abaixo:
```sql
-- Retorna todos os registros que na coluna name começa com 'web'
SELECT * FROM products WHERE name Like 'web%'
```
- Mas se passarmos no inicio e no final, ele pesquisa em qualquer parte da palavra, como no exemplo a seguir:
```sql
-- Retorna todos os registros que na coluna name tem a letra 'a'
SELECT * FROM products WHERE name LIKE '%a%'
```