___
- Quando usamos o Spring Boot, ele vai ver apenas o pacote final da aplicação, mas caso queiramos usar outro pacote externo a esse pacote final, passamos uma `annotation`, para a classe principal, onde contém o `@SpringBootApplication`
```java
@SpringBootApplication
@ComponentScan(basePackages = "br.com.groupid")
public class Projeto {
	// Código...
}
```
- O `@ComponentScan()`, ao passarmos o `basePackages` e informamos o `groupId`, o Spring vai escanear todos os pacotes do grupo, e assim vai incluir na aplicação;