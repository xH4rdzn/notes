___
### Inserindo registros
- A sintaxe de inserção de novos registros em uma tabela é bem simples, basta seguir o exemplo abaixo:
```sql
INSERT INTO nome_da_tabela VALUES(valor1, valor2, ..., valorN);
```
- Ou
```sql
INSERT INTO nome_da_tabela(coluna1, ..., colunaN) VALUES(valor1, ..., valorN);
```
- Exemplos:
```sql
INSERT INTO user_type VALUES(null, 'ALUNO', null);
INSERT INTO user_type VALUES(null, 'PROFESSOR', null);
INSERT INTO user_type VALUES(null, 'ALUNO', null);
```

### Alterando registros
- Para alterar algum registro, basta utilizar o comando ***`UPDATE`*** seguindo do nome da tabela, apontar os campos que serão atualizados e informar para qual registro que será alterado.
```sql
UPDATE nome_da_tabela
	SET coluna1 = valor1,
		coluna2 = valor2,
		...,
		colunaN = valorN
WHERE colunaX = ?;
```

### Excluindo registros
- Para deletar usamos como no exemplo abaixo:
```sql
DELETE FROM nome_da_tabela;
```
- Se não passarmos uma condição, todos os registros da tabela serão apagados;
- Então sempre usamos uma condição:
```sql
DELETE FROM nome_databela WHERE condição;
```
- Como no exemplo abaixo:
```sql
DELETE FROM users WHERE id = 7;

DELETE FROM users WHERE name LIKE 'Ma%'
```