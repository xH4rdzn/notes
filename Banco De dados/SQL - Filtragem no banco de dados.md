___
## 1. Selecionar Dados

```sql
SELECT coluna1, coluna2 FROM tabela WHERE condição;
```

Exemplo: Seleciona todos os nomes e idades da tabela de clientes onde a idade é maior que 18.

```sql
SELECT nome, idade FROM clientes WHERE idade > 18;
```

## 2. Inserir Dados

```sql
INSERT INTO tabela (coluna1, coluna2) VALUES (valor1, valor2);
```

Exemplo: Insere um novo cliente na tabela de clientes com nome e idade.

```sql
INSERT INTO clientes (nome, idade) VALUES ('João', 25);
```
## 3. Atualizar Dados

```sql
UPDATE tabela SET coluna1 = valor1 WHERE condição;
```

Exemplo: Atualiza a idade de um cliente com o nome 'João' para 30.

 ```sql
UPDATE clientes SET idade = 30 WHERE nome = 'João';
 ```

## 4. Deletar Dados

```sql
DELETE FROM tabela WHERE condição;
```

Exemplo: Deleta todos os clientes que possuem idade menor que 18.

```sql
DELETE FROM clientes WHERE idade < 18;
```

## 5. Ordenar Resultados

```sql
SELECT coluna1, coluna2 FROM tabela ORDER BY coluna1 ASC/DESC;
```

Exemplo: Seleciona todos os clientes ordenados pela idade em ordem decrescente.

```sql
SELECT * FROM clientes ORDER BY idade DESC;
```

## 6. Agrupar Resultados

```sql
SELECT coluna, COUNT(*) FROM tabela GROUP BY coluna;
```

Exemplo: Conta quantos clientes existem em cada cidade.

```sql
SELECT cidade, COUNT(*) FROM clientes GROUP BY cidade;
```
## 7. Consultas com Junções (JOIN)

```sql
SELECT tabela1.coluna1, tabela2.coluna2 FROM tabela1 JOIN tabela2 ON tabela1.coluna_comum = tabela2.coluna_comum;
```

Exemplo: Seleciona os pedidos e os nomes dos clientes de uma tabela de pedidos e uma tabela de clientes.

 ```sql
SELECT pedidos.pedido_id, clientes.nome FROM pedidos
JOIN clientes ON pedidos.cliente_id = clientes.id;
 ```

## 8. Consolidando valores SUM()

- Quando quisermos consolidar um valor, ou seja somar os valores de uma tabela usamos a função `SUM()`.
```sql
SELECT SUM(coluna) FROM tabela
```
- Também podemos fazer filtros com o `WHERE`
```sql
SELECT SUM(coluna) FROM tabela WHERE condição;
```
- Podemos também agrupar esses valores separados por um filtro, como no exemplo abaixo:
```sql
SELECT coluna, SUM(colunaValor) FROM tabela GROUP BY coluna HAVING SUM(colunaValor)
```