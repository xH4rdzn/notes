___
- Esses operadores podem somar [[Filtrando valores|filtros]], então usamos o comando `AND` ou `OR`
- O operador `AND`, tem que ser satisfeito os dois critérios
```sql
SELECT * FROM products WHERE price > 500 AND price < 1000
```
- Podemos adicionar quantos filtros precisarmos.
- Quando usamos o operador `OR`, apenas um dos critérios precisam ser satisfeitos
```SQL
SELECT * FROM products WHERE price > 500 OR price < 1000
```