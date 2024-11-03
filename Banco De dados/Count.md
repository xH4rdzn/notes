___
- O comando `COUNT`, retorna a soma dos registros que são encontrados de acordo com os filtros passados.
```sql
-- Retorna a soma de registros que a tabela products possui
SELECT COUNT(*) FROM products
```
- Podemos usar passando filtros também, como no exemplo:
```sql
SELECT COUNT(*) FROM products WHERE price >= 600
```