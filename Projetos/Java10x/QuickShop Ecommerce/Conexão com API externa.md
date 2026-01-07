___
- Como não temos acesso ao banco de dados onde se encontra os produtos, vamos ter que fazer o acesso a partir de uma API externa.
- Para isso, vamos criar um ***package controller*** e vamos criar o *ProductController* e dentro dele vamos fazer:
```java
@RestController
@RequestMapping("/products")
public class ProductController {

	private final ProductService productService;
	
	public ProductController(ProductService productService) {
		this.productService = productService;
	}

	@GetMapping
	public ResponseEntity<Void> getAllProducts() {}
	
	
	@GetMapping("/{id}")
	public ResponseEntity<Void> getProductsById(@PathVariable Long id) {}
 }
```
- Agora vamos criar o ***package service*** e dentro dele vamos criar o nosso *ProductService*
```java
@Service
public class ProductService {
	
	public void getAllProducts() {}

	public void getProductsById(Long id) {}
}
```
- Agora para podermos consumirmos a nossa *API* externa, vamos criar um *package client*, e dentro dele vamos criar o arquivo com o nome da API que vamos consumir.
```java
@FeignClient(name = "PlaziStoreClient", url = "${basket.client.plazi}")
public interface PlaziStoreClient {
	public void getAllProcucts();
	
	public void getProductById(Long id);
}
```
- Porém a url, vamos passar em nossas variáveis ambientes, então em nosso arquivo *application.yml*, vamos adicionar:
```yml
basket:
	client:
		plazi: https://api.escuelajs.co/api/v1
```
- Agora em nossa *interface*, precisamos anotar com os métodos que queremos que ele faça as chamadas:
```java
@FeignClient(name = "PlaziStoreClient", url = "${basket.client.plazi}")
public interface PlaziStoreClient {
	
	@GetMapping("/products")
	public void getAllProcucts();
	
	@GetMapping("/products/{id}")
	public void getProductById(@PathVariable Long id);
}
```
- Agora precisamos montar o nosso objeto de resposta, para isso dentro do *package client*, vamos criar o *package response*, e dentro dele vamos criar um *record PlaziProductResponse*
```java
public record PlaziProductResponse(Long id, String title, BigDecimal price) {}
```
- Como o primeiro método da nossa interface retorna uma lista de produtos, precisamos alterar o método para o seguinte:
```java
@GetMapping("/products")
List<PlaziProductResponse> getAllProducts();
```
- E o método que procuramos um produto por ID, retorna apenas um, então o alteramos para:
```java
@GetMapping("/products/{id}")
PlaziProductResponse getProductById(@PathVariable Long id);
```
- Agora voltamos a nossa *ProductService* e injetamos o nosso *client*, como é demonstrado no exemplo abaixo:
```java
private final PlaziStoreClient plaziStoreClient;

public List<PlaziProductResponse> getAllProducts() {
	return plaziStoreClient.getAllProducts();
}

public PlaziProductResponse getProductById(Long id) {
	return plaziStoreClient.getProductById(id);
}
```
- E agora em nossa *Controller*, vamos fazer a chamada para a nossa *Service*
```java
@GetMapping
public ResponseEntity<PlaziProductResponse> getAllProducts() {
	return ResponseEntity.ok(productService.getAllProducts());
}

@GetMapping("/{id}")
public ResponseEntity<PlaziProductResponse> getProductById(@PathVariable Long id) {
	return ResponseEntity.ok(productService.getProductById(id));
}
```
- Agora em nosso arquivo principal da nossa aplicação, precisamos adicionar a anotação:
```java
@EnableFeignClient
```
- Agora podemos executar a nossa aplicação, e testar.