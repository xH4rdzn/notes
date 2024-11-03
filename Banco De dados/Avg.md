___
- O comando `AVG`, é utilizado para fazer médias de valores.
```sql
SELECT AVG(price) FROM products
```
- Podemos usar o `AVG`, com filtros
```sql
SELECT AVG(price) FROM products WHERE category = 'audio'
```