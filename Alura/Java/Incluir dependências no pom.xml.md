___
- Para adicionar dependências no projeto Spring no qual usamos o `Maven`, é bem simples;
1. Acessamos o site: [Maven Repository](https://mvnrepository.com/)
2. Buscamos a dependência na qual queremos;
3. Escolhemos a versão que vamos utilizar;
4. Copiamos o código e colamos em nosso arquivo `pom.xml`, como no exemplo que possui o código da dependência Jackson
```xml
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-databind</artifactId>
    <version>2.18.1</version>
</dependency>
```
5. Após isso basta carregarmos o `Maven`, e pronto nossa dependência já vai estar pronta para uso;