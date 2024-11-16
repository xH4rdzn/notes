___
- O Controller é onde criamos os `endpoints` da nossa aplicação;
- O Controller é responsável por identificar qual `endpoint` está sendo chamado e executa a função;
- Para criar uma controller fazemos da seguinte maneira:
```java

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.bind.annotation.GetMapping;

@RestController
@RequestMapping("/endereco")
public class Controller {

	@GetMapping("/exemplo")
	public String primeiroMetodo() {
		return "Meu primeiro método api rest";
	}
}
```
- O `@RequestMapping`, é o endereço onde esse Controller vai *atender* as requisições;
- O `@RestController`, é para o Spring Boot gerenciar esse Controller;
- O `@GetMapping` é o método HTTP que vamos utilizar na rota, nele passamos o endereço onde esse método vai atender;