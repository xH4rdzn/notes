___
- Agora vamos criar as tabelas do nosso banco de dados, para isso, dentro do *package* principal, vamos criar o *package* de **entity**, nesse pacote vamos colocar todos arquivos que serão uma entidade(tabela) em nosso banco de dados.
- Abaixo temos o exemplo da entidade `category`
```java
@Getter
@Setter
@Entity
@Table(name = "category")
public class Category {
	
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long id;

	@Column(length = 100, nullable = false)
	private String name;
}
```
- E agora criamos um novo *package*, agora para os nossos repositórios, para isso vamos criar o *package* ***repository***, e dentro dele vamos seguir o exemplo:
```java
package br.com.movieflix.repository;

// importações

@Repository
public interface CategoryRepository extends JpaRepository<Category, Long> {}
```
- ***Nota-se que onde está `Category`é a classe na qual se refere a nossa entidade e o segundo parâmetro é o tipo do nosso `id`***
- ***O `@Repository` não é obrigatório;
- Agora vamos criar um *package* para os nossos serviços, o ***package service*** e nele vamos criar os serviços relacionados a categoria(`CategoryService`)
```java
package br.com.movieflix.service;  
  
import org.springframework.stereotype.Service;  
  
@Service  
public class CategoryService {  
}
```
- ***A camada `service`, é apenas para a nossa regra de negócio, as chamadas são feitas em outra camada;
- Agora vamos criar o *package* para os `controllers`que é onde vão ser recebidos as nossas chamadas HTTP
- Criamos o *package* com o nome de `controller
- Dentro dela criamos os arquivos, nesse exemplo o `CategoryController`e fazemos como no exemplo abaixo:
```java
package br.com.movieflix.controller;  
  
import org.springframework.web.bind.annotation.RequestMapping;  
import org.springframework.web.bind.annotation.RestController;  
  
@RestController  
@RequestMapping("/movieflix/category")  
public class CategoryController {  
}
```
- Como em nosso *controller*, provavelmente vamos precisar da nossa camada de *service*, precisamos fazer a injeção dessa dependência, para isso temos 3 maneiras:
1. Usando o `@Autowired`
```java
package br.com.movieflix.controller;  
  
import org.springframework.web.bind.annotation.RequestMapping;  
import org.springframework.web.bind.annotation.RestController;  
  
@RestController  
@RequestMapping("/movieflix/category")  
public class CategoryController { 

	@Autowired
	private final CategorySerice categoryService; 
}
```
2. Criando um construtor para a classe
```java
package br.com.movieflix.controller;  
  
import org.springframework.web.bind.annotation.RequestMapping;  
import org.springframework.web.bind.annotation.RestController;  
  
@RestController  
@RequestMapping("/movieflix/category")  
public class CategoryController { 

	private final CategorySerice categoryService; 
	
	public CategoryController(CategoryService categoryService) {
		this.categoryService = categoryService;
	}
}
```
3. Usando a `@RequiredArgsConstructor`, nesse caso apenas quando estivermos usando o ***Lombok***
```java
package br.com.movieflix.controller;  
  
import org.springframework.web.bind.annotation.RequestMapping;  
import org.springframework.web.bind.annotation.RestController;  
  
@RestController  
@RequestMapping("/movieflix/category")
@RequiredArgsConstructor  
public class CategoryController { 

	private final CategorySerice categoryService; 

}
```
- ***Podemos usar essa maneira nas outras camadas, caso precisamos fazer a injeção de dependências***
- 