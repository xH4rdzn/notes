___
- Para atualizar dados, usamos o comando `UPDATE`, como demonstra no exemplo abaixo:
```sql
UPDATE products SET price = 45.90, category = 'acessory' WHERE id = 1
```
- Não podemos esquecer de especificar qual registro queremos mudar com o comando `WHERE`, caso contrário irá mudar todos os registros do banco de dados.