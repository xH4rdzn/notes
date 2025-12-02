___
 - Para adicionar, a documentação com o *Open API Swagger*, precisamos adicionar o código abaixo em nosso arquivo `pom.xml`
```xml
<dependency>
    <groupId>org.springdoc</groupId>
    <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
    <version>2.2.0</version>
</dependency>
```
- Agora em nosso arquivo `application.yaml`, vamos precisar adicionar a seguinte configuração:
```yaml
springdoc:
	api-docs:
		path: /api/api-docs
	swagger-ui:
		path: /swagger/index.html	
```
- Como estamos utilizando o *`Spring Security`*, precisamos fazer a liberação desse caminho em nosso `SecurityConfig`, como no exemplo abaixo:
```java
// abaixo de qualquer requestMatchers()
.requestMatchers(HttpMethod.GET, "/api/api-docs/**").permitAll()
.requestMatchers(HttpMethod.GET, "/swagger/**").permitAll()
```
- Agora dentro do nosso pacote de `Config`, vamos criar a classe `SwaggerConfig`, e fazer como demonstrado abaixo:
```java
@Configuration
public class SwaggerConfig {
	
	@Bean
	public OpenAPI getOpenAPI {
		
		Contact contact = new Contact();
		contact.name("Igor");
		contact.email("xh4rdzn@gmail.com");
		
		Info info = new Info();
		info.title("MovieFlix");
		info.version("v1");
		info.description("Aplicação para gerenciamento de catalog de filmes")
		info.contact(contact);
		
		
		return new OpenAPI().info(info);
	}
	
}
```
- Agora se acessarmos as url's configuradas vamos ter acesso a documentação *api-docs* em JSON, e *swagger-ui/index.html* para a tela personalizada que vai conter os dados da nossa documentação.
- Podemos personalizar ainda mais essa documentação.
- Para isso podemos ir nas *controllers* e adicionar as anotações
```java
// Adicionamos antes da declaraçã da classe
@Tag(name = "Movie", description = "Recurso responsável pelo gerenciamento dos filmes")

// Nos métodos utilizamos o @Operation e o @ApiResponse
@Operation(summary = "metodo", description = "descrição do método")
@ApiResponse(responseCode = "200", description = "descrição do retorno", content = @Content = @Schema(implementation = ClasseDeRetorno.class)))
```