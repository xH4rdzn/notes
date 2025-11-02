___
- Quando tivermos um ***Bean*** onde é implementado uma *interface*, podemos ter mais de uma classe concreta que faz o uso dessa interface.
- E quando fazemos a injeção de dependência diretamente da interface, o *spring*, vai dar erro ao tentar iniciar a nossa aplicação pois existem dois *beans* que fazem o uso dessa interface

### @Primary
- Usamos essa anotação, para que essa implementação de interface seja considerada a padrão em nossa aplicação.
- Então agora mesmo que tenhamos mais de uma implementação da *interface*, a nossa aplicação vai fazer uso da classe concreta que está utilizando essa anotação
```java
@Primary
@Component
public class StandardShippingCaclculator implements ShippingCalculator {

	// Código a ser implementado

}
```

### Nomenado Beans
- Podemos dar nomes para os nossos *beans*, para fazer isso ao adicionar a anotação `@Component`, passamos o nome como parâmetro dessa anotação
```java
@Component(value = "expressShippingCaclculator")
public class ExpressShippingCalculator implements ShippingCaclculator {

	// Código de implementação
}
```

### @Qualifier
- Essa anotação é usada para distinguir as implementações quando temos uma injeção de dependência que faz o uso da mesma *interface*, então passamos o nome do *bean* que queremos usar como parâmetro dessa anotação, como é demonstrado no exemplo abaixo:
```java
@Service
public class ShippingService {

	private final ShippingCalculator standardCaclculator;
	private final ShippingCalculator expressCalculator;
	
	
	public ShippingService(@Qualifier("standardShippingCalculator") ShippingCalculator standardCalculator, @Qualifier("expressShippingCalculator") ShippingCalculator expressCalculator) {
		this.standardCalculator = standardCalculator;
		this.expressCaclculator = expressCalculator;
	
	}
}
```