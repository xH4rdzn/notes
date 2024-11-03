___
- Dentro do programa `Beekeeper`, vamos criar a nossa primeira tabela com o código abaixo:
```sql
CREATE TABLE products
```
- Por padrão os comandos `sql`, são maiúsculos. 
- Quando temos nomes compostos, usamos o `_` para separar as palavras, como no exemplo abaixo
```sql
CREATE TABLE products_categories
```
- Para criar as colunas na tabela fazemos da seguinte maneira:
```sql
CREATE TABLE products (
	id INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
	name TEXT NOT NULL,
	price REAL NOT NULL,
	category TEXT NULL DEFAULT 'general'
)
```
- `NOT NULL` -> esse campo não aceita valores nulos
- `AUTOINCREMENT`-> esse campo é incremental, o próprio banco de dados vai gerenciar esse valor.
- `DEFAULT` -> Definimos um valor padrão para a tabela