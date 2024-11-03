___
- Usamos o comando `WHERE`, para filtrar, passamos condições para trazer apenas dados que satisfazem essa condição.
- Usamos o `WHERE`, da seguinte maneira:
- Com igualdade
```sql
-- Retorna todos os dados onde a coluna 'name' tem o valor 'Mouse'
SELECT * FROM products WHERE name = 'Mouse'
```
- Lembrando que é `CASE SENSITIVE`, em outras palavras minúscula e maiúscula tem diferença;