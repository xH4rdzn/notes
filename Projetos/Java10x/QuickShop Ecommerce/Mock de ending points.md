___
- Para criar uma entidade, utilizando o *MongoDB*, utilizamos a anotação ***`@Document`***, então podemos fazer como no exemplo abaixo:
```java
@Getter
@Setter
@NoArgsConstructor
@AllArgsConstructor
@Builder
@Document(collection = "basket")
public class Basket {
	
	@Id
	private String id;
	
	private Long client;
	
	private BigDecimal totalPrice;
	
	private List<Product> products;
	
	private Status status;
	
	public void calculateTotalPrice() {
		this.totalPrice = products.stream()
			.map(product -> product.getPrice().multiply(BigDecimal.valueOf(product.getQuantity())))
			.reduce(BigDecimal.ZERO, BigDecimal::add)
	}
}
```
- Agora precisamos criar o nosso `Product`:
```java
@Getter
@Setter
public class Product {
	
	private Long id;
	
	private String title;
	
	private BigDecimal price;
	
	private Integer quantity;
}
```
- E o nosso *enum* de `Status`
```java
public enum Status {
	OPEN, SOLD
}
```
- Agora o nosso **repository**, criamos da seguinte maneira:
```java
public interface BasketRepository extends MongoRepository<Basket, String> {}
```
- A nossa **Service**:
```java
@Service
@RequiredArgsConstructor
public class BasketService {
	
	private final BasketRepository basketRepository;
	
	
	// Criar a Basket
	public Basket createBasket(BasketRequest basket) {
		
	}

}
```
- Agora para criar a nossa **controller**, fazemos:
```java
@RestController
@RequestMapping("/basket")
@RequiredArgsConstructor
public class BasketController {

	private final BasketService basketService;
	
	
	@PostMapping
	public ResponseEntity<Basket> createBasket(@RequestBody BaksetRequest request) {
		return ResponseEntity.status(HttpStatus.CREATED).body(basketService.createBasket(request));
	}

}
```