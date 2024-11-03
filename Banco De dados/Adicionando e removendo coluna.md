___
- Já [[Criando tabela via código - SQL|criamos]] a nossa tabela via código, agora vamos aprender a adicionar e remover colunas nas tabelas.
```sql
ALTER TABLE products ADD quantity INTEGER NOT NULL
```
- `ALTER` -> para alterar;
- `TABLE` -> tabela
- `ADD` -> adicionar uma coluna;
- Para remover uma coluna também usamos o `ALTER TABLE`, como no exemplo a seguir:
```sql
ALTER TABLE products DROP COLUMN quantity
```
- `DROP COLUMN` -> indica qual tabela queremos remover;