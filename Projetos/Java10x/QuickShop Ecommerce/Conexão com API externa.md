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