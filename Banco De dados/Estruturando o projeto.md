___
### Criando o banco de dados
- A sintaxe de criação de um baco de dados é bem simples e intuitiva e se você tiver um pouco de conhecimento da língua inglesa fica mais fácil ainda de entender.
```sql
CREATE DATABASE rasmoo_plus;
```
- Depois é criado, é necessário informar ao MySQL que ele será utilizado.
```sql
USE rasmoo_plus;
```
- Feito isso, o banco de dados está criado e pronto para uso. Agora está faltando somente criar as tabelas.
### Criando as tabelas
- Para criar uma tabela basta utilizar o comando ***`CREATE TABLE`*** e colocar em prática tudo aquilo que foi aprendido sobre tipos de dados.
```sql
CREATE TABLE user_type(
	id INT PRIMARY KEY AUTO_INCREMENT,
	name VARCHAR(100) NOT NULL UNIQUE,
	description TEXT
);

-- Outra tabela
CREATE TABLE users(
	id INT PRIMARY KEY AUTO_INCREMENT,
	name VARCHAR(100) NOT NULL,
	email VARCHAR(150) NOT NULL UNIQUE,
	phone VARCHAR(13) NOT NULL,
	cpf VARCHAR(11) NOT NULL UNIQUE,
	user_type_id INT NOT NULL,
	FOREIGN KEY(user_type_id) REFERENCES user_type(id)
);
```
