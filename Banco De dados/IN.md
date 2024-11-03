___
- Usamos o `IN`, para fazer filtro aplicando múltiplos valores. Como no exemplo a seguir:
```sql
SELECT * FROM products WHERE price IN (800, 550)
```
- Podemos passar mais parâmetros, só precisamos separar eles por `,`
- E podemos usar para textos também
```sql
SELECT * FROM products WHERE category IN ('image', 'audio')
```