___
- Quando usamos o `<>`, significa diferente, nesse caso retorna todos os registros que é diferente da condição passada
```sql
-- Seleciona valores diferentes
SELECT * FROM products WHERE price <> 800
```
- Quando queremos buscar por registros que tem uma condição maior do que a que passamos usamos o `>`.
```sql
SELECT * FROM products WHERE price > 300
```
- Se quisermos buscar por registros que tem uma condição menor do que a que passamos usamos o `<`.
```SQL
SELECT * FROM products WHERE price < 300
```
- Podemos usar o `>=`, que retorna todos os registros que são maior ou igual a condição que passamos
```sql
SELECT * FROM products WHERE price >= 500.50
```
- Assim como temos o `>=`, temos também o `<=`, que retorna todos os registros que possui a condição menor ou igual a que passamos.
```sql
SELECT * FROM products WHERE price <= 800
```