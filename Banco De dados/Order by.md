___
- Esse comando serve para organizar os registros retornados pelo comando `SELECT`.
- Usamos ele para ordenar, como no exemplo a seguir que ordenamos pelo `price`
```sql
SELECT * FROM products ORDER BY price
```
- Ele organiza do menor para o maior, mas podemos alterar essa ordem usando o comando `DESC`
```sql
-- DESC (decrescente)
SELECT * FROM products ORDER BY price DESC
```
- Por padrão ele já vem de maneira crescente, mas se quisermos deixar explicito usamos o `ASC`
```sql
-- ASC (crescente)
SELECT * FROM products ORDER BY price ASC
```
- Conseguimos também fazer filtros, usando o `Order by`. Fazemos da seguinte maneira:
```sql
SELECT * FROM products WHERE category = 'audio' ORDER BY price DESC
```
- Podemos usar o `ORDER BY`, com textos também, dessa maneira ele organiza de maneira alfabética.
```sql
SELECT * FROM products ORDER BY name
```