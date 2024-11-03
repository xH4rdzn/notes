___
- O comando `SUM`, é utilizado para fazer somas, como no exemplo que queremos somar todos os valores da coluna `price`. Fazemos da seguinte maneira:
```sql
SELECT SUM(price) FROM products
```
- Podemos utilizar filtros também
```sql
SELECT SUM(price) FROM products WHERE category = 'audio'
```
- Esse comando, só é utilizado em colunas que possuem valores numéricos; 