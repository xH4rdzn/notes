___
### Inicinado o projeto no Spring Initialzr
1. Primeiro vamos no site do [Spring Initialzr](https://start.spring.io/)
2. Fazemos as configurações e vamos adicionar as dependências:
	- Spring Web
	- Spring Data MongoDB
	- OpenFeign
3. Agora podemos gerar o nosso projeto em *.zip* e abrir em nossa IDE.
4. Agora precisamos incluir a dependência do ***OpenCSV***, para isso vamos abrir o arquivo `pom.xml`
5. Agora vamos no site [Maven Repository](https://mvnrepository.com/) para adicionarmos a dependência do ***OpenCSV***
```xml
<dependency>
    <groupId>com.opencsv</groupId>
    <artifactId>opencsv</artifactId>
    <version>5.12.0</version>
</dependency>
```
- Desta maneira, basta fazermos uma atualização