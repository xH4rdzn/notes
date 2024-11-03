___
- Quando queremos inserir mais de uma linha precisamos usar o `;`
```sql
INSERT INTO products (name, price, category) VALUES ('Microfone', 550, 'audio');
INSERT INTO products (name, price, category) VALUES ('Webcam', 1200, 'image');
INSERT INTO products (name, price, category) VALUES ('Headset', 800, 'audio');
```
- Para remover dados de uma tabela usamos o comando `DELETE FROM`, como demonstra o exemplo abaixo:
```sql
DELETE FROM products WHERE id = 3
```
- **NÃO PODEMOS ESQUECER DE USAR O WHERE, caso contrário irá apagar todos os registros da tabela.**