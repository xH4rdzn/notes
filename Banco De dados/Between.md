___
- Usamos o comando `Between` para fazer um filtro em um intervalo de valores. Como no exemplo a seguir:
```sql
-- Usando os operadores AND
SELECT * FROM products WHERE price >= 600 AND price <= 1200

-- Usando o Between
SELECT * FROM products WHERE price BETWEEN 600 AND 1200
```