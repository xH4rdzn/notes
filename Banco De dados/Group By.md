___
- O comando `GROUP BY`, serve para agrupar registros.
- Podemos usar como nos exemplos abaixo:
```sql
SELECT category, COUNT(*) FROM products GROUP BY category

-- Usando o Aliases
SELECT category, COUNT(*) AS TOTAL FROM products GROUP BY category

-- Usando com ORDER BY
SELECT category, COUNT(*) AS total
FROM products 
GROUP BY category 
ORDER BY total DESC

-- Usando com WHERE
SELECT category, COUNT(*) AS total
FROM products 
WHERE price > 600
GROUP BY category 
ORDER BY total DESC
```