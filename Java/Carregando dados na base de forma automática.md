___
- O ***`spring`***, tem suporte para dois tipos de scripts, um se chama `data.sql`e o outro é o `schema.sql`, colocamos esses arquivos dentro da pasta **`resources`**;
- Dessa forma ao subirmos nossa aplicação cada arquivo teria uma responsabilidade:
	- ***`schema.sql`*** -> responsável por fazer a criação das nossas tabelas
	- ***`data.sql`*** -> tem com o objetivo de fazer a inserção de dados que são fixos dentro do nosso banco de dados de forma automática.
- Para tudo isso funcionar em nosso arquivo ***`application.properties`*** adicionamos as seguintes linhas
```properties
spring.sql.init.mode=always
spring.jpa.defer-datasource-initialization=true
```
- A primeira propriedade significa que toda vez que formos subir a nossa aplicação ele vai rodar os arquivos `data.sql`e `schema.sql`
- A segunda propriedade quer dizer que vamos fazer o uso desses scripts de uma forma um pouco mais tardia. Para não dar conflito com o ***Hibernate***.
- Agora dentro do nosso arquivo de ***`data.sql`***, vamos fazer o script para inserir dados em nossas tabelas
```sql
-- tb_products
INSERT INTO tb_products (product_id, product_name, price)
	VALUES
		(1, 'Computer', 4500.50),
		(2, 'Smartphone', 2000.00),
		(3, 'Mouse', 200.00)
	ON CONFLICT (product_id) DO NOTHING;
	
-- tb_tags
INSERT INTO tb_tags (tag_id, name)
	VALUES
		(1, 'Eletronics'),
		(2, 'Home'),
		(3, 'Apple')
	ON CONFLICT (tag_id) DO NOTHING;
	
-- tb_products_tags
INSERT INTO tb_products_tags (product_id, tag_id)
	VALUES
	(1, 1),
	(2, 3),
	(2, 1),
	(3, 1)
	ON CONFLICT (product_id, tag_id) DO NOTHING;	
```
- Dessa maneira ao subirmos a nossa aplicação ele vai inserir os dados em nosso banco de dados e ao reiniciarmos a aplicação ele não vai fazer a duplicata dos dados;