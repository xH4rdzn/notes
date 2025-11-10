___
- Para cadastrar pedidos, vamos fazer um ***controller*** seperado para ela, nesse caso dentro do ***`package controllers`*** vamos criar o arquivo `OrderController`, e vamos fazer a implementação dele da seguinte maneira:
```java
@RestController
@RequestMapping(path = "/orders")
public class OrderController {}
```
- Como vamos ter que acessar o ***`repository`*** e o ***`service`***, vamos criar eles:
```java
// Repositorios
public interface OrderRepository extends JpaRepository<OrderEntity, Long> {}

public interface ProductRepository extends JpaRepository<ProductEntity, Long> {}

public interface OrderItemRepository extends JpaRepository<OrderItemEntity,OrderItemId> {}

public interface TagRepository extends JpaRepository<TagEntity, Long> {}

// Services
@Service
public class OrderService {
	
	private final UserRepository userRepository;
	private final OrderRepository orderRepository;
	private final ProductRepository productRepository;
	private final OrderItemRepository orderItemRepository; 
	
	// construtor
	
	public OrderEntity createOrder() {
		return null;
	}
	
}
```
- Voltando ao nosso `controller`, vamos injetar a nossa `service`e criar o método para fazer a criação desse pedido
```java
@RestController
@RequestMapping(path = "/orders")
public class OrderController {

	@PostMapping
	public ResponseEntity<Void> createOrder(@RequestBody CreateOrderDTO dto) {}

}
```
- Agora precisamos definir o que o nosso *`DTO`* precisa para podermos cadastrar um novo pedido, deixando ele da seguinte maneira:
```java
public record CreateOrderDTO(UUID userId,
							List<OrderItemDTO> items)
```
- E dentro desse outro *`DTO`*, vamos receber a quantidade e o Id do produto
```java
public record OrderItemDTO(Integer quantity, Long productId) {}
```
- Agora em nossa service, vamos fazer o seguinte:
```java
@Service
public class OrderService {
	
	private final UserRepository userRepository;
	private final OrderRepository orderRepository;
	private final ProductRepository productRepository; 
	
	// construtor
	
	public OrderEntity createOrder(CreateOrderDTO dto) {
		
		var order = new OrderEntity();
		
		var user = validateUser(dto);
		
		var orderItems = validateOrderItems(order,dto);
		
		var total = calculateOrderTotal(orderItems);
		
		order.setOrderDate(LocalDateTime.now());
		order.setUser(user);
		order.setItems(orderItems);
		order.setTotal(total);
		
		
		return orderRepository.save(order);
		
	
	}
	
	private UserEntity validateUser(CreateOrderDTO dto) {
		userRepository.findById(dto.userId())
			.orElseThrow(() -> new CreateOrderException("User not found"));
	}
	
	private List<OrderItemEntity> validateOrderItem(OrderEntity order, CreateOrderDTO dto) {
		
		if(dto.items().isEmpty()) {
			throw new CreateOrderException("Order items is empty");
			
			return dto.items().stream()
				.map(orderItemDTO -> getOrderItem(order, orderItemDTO))
				.toList();
		}
		
	}
	
	private OrderItemEntity getOrderItem(OrderEntity order, OrderItemDTO orderItemDTO) {
		var orderItemEntity = new OrderItemEntity();
		var id = new OrderItemId();
		var product = getProduct(ordemItemDTO.productId());
		
		id.setOrder(order);
		id.setProduct(product);
		
		orderItemEntity.setId(id);
		
		orderItemEntity.setQuantity(orderItemDTO.quantity());
		orderItemEntity.setSalePrice(product.getPrice());
		
		
		return orderItemEntity;
	}
	
	
	private ProductEntity getProduct(Long productId) {
		return productRepository.findById(productId)
			.orElseThrow(() -> new CreateOrderException("product not found"));
	}
	
	private BigDecimal calculateOrderTotal(List<OrderItemEntity> items) {
	
		return items.stream()
			.map(i -> i.getSalePrice().multiply(BigDecimal.valueOf(i.getQuantity())))
			.reduce(BigDecimal::add)
			.orElse(BigDecimal.ZERO);
	
	
	}
	
	
	
}
```