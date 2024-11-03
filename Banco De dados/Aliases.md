___
- O comando `AS`, serve apenas para dar um nome temporário a uma coluna.
- Como no exemplo a seguir:
```sql
-- Com ''
SELECT COUNT(*) AS 'TOTAL' FROM products

-- Sem ''
SELECT COUNT(*) AS TOTAL FROM products

-- O AS é opcional
SELECT COUNT(*) TOTAL FROM products
```
- Para passar nomes compostos passamos o nome que queremos entre `''` ou `[]`;
```sql
-- Nome Composto
SELECT COUNT(*) AS 'TOTAL DE PRODUTOS' FROM products

-- Com []
SELECT COUNT(*) AS [TOTAL DE PRODUTOS] FROM products
```
- Esses nomes são apenas para exibição, não alteram o nome no banco de dados em si.