___
- Quando temos uma tabela com um relacionamento com uma outra tabela ou outras tabelas, sempre vamos ter uma chave estrangeira, que é uma coluna de conexão.
- O comando `INNER JOIN`, retorna os registros onde existe uma correspondência em ambas as tabelas.
```sql
SELECT a.id, a.student_id, a.street, a.city, s.name
FROM student_adress AS a
INNER JOIN students AS s ON s.id = a.student_id
```
- `ON` -> Serve para definir qual coluna, vamos usar para fazer essa conexão;
- Usamos os nomes renomeados para retornar os dados, caso contrário pode dar erro de ambiguidade;

### Exemplos
- Exemplo 1: Obter pedidos com os dados do cliente
```sql
SELECT 
    clientes.nome,
    pedidos.id_pedido,
    pedidos.data_pedido,
    pedidos.total
FROM 
    pedidos
INNER JOIN 
    clientes ON pedidos.id_cliente = clientes.id_cliente;

```
- Exemplo 2: Filtrar pedidos por cidade do cliente
```sql
SELECT 
    clientes.nome,
    clientes.cidade,
    pedidos.id_pedido,
    pedidos.total
FROM 
    pedidos
INNER JOIN 
    clientes ON pedidos.id_cliente = clientes.id_cliente
WHERE 
    clientes.cidade = 'São Paulo';

```
- Exemplo 3: Total gasto por cliente (com agrupamento)
```sql
SELECT 
    clientes.nome,
    SUM(pedidos.total) AS total_gasto
FROM 
    pedidos
INNER JOIN 
    clientes ON pedidos.id_cliente = clientes.id_cliente
GROUP BY 
    clientes.nome;

```
- Exemplo 4: Com 3 tabelas
```sql
SELECT 
    clientes.nome AS cliente,
    pedidos.id_pedido,
    produtos.nome_produto,
    itens_pedido.quantidade,
    produtos.preco,
    (itens_pedido.quantidade * produtos.preco) AS total_item
FROM 
    pedidos
INNER JOIN 
    clientes ON pedidos.id_cliente = clientes.id_cliente
INNER JOIN 
    itens_pedido ON pedidos.id_pedido = itens_pedido.id_pedido
INNER JOIN 
    produtos ON itens_pedido.id_produto = produtos.id_produto;

```
- A *QUERY* acima deve retornar uma lista detalhada dos produtos comprados por cada cliente, com quantidade e total por item