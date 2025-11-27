___
- Após fazer o endpoint para cadastrar um usuário, agora vamos fazer a implementação do ***Spring Security***.
- Apenas adicionando essa dependência, todos os endpoints da nossa aplicação ficam bloqueados, pela configuração padrão.
- Para podermos configurar o ***Spring Security***, vamos criar classes que são *configurações*, para isso precisamos criar uma *package*, com o nome ***`config`***.
- Dentro desse *package* agora podemos criar a classe `SecurityConfig`, como no exemplo abaixo:
```java
public class SecurityConfig {}
```
- Como ela é uma classe de configuração, precisamos anotar essa classe com o `@Configuration`, ficando da seguinte maneira:
```java
@Configuration
public class SecurityConfig {}
```
- E também precisamos usar a anotação `@EnableWebSecurity`, essa anotação basicamente diz como funciona o login e autenticação da nossa aplicação.
```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {}
```
- Agora precisamos fazer a implementação do método `securityFilterChain`, que é um `@Bean`, como no exemplo abaixo:
```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {

	
	@Bean
	public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
		
		return http
		.csrf(csrf -> csrf.disable())
		.sessionManagement(session -> session.sessionCreatePolicy(SessionCreationPolicy.STATELESS))
		.authorizeHttpRequests(authorize -> 
			.requestMatchers(HttpMethod.POST, "/auth/register").permitAll()
			.requestMatchers(HttpMethod.POST, "auth/login").permitAll()
			.anyRequest().authenticated()
		)
		.build();
		
	}

}
```
- Agora precisamos fazer a criptografia da senha do nosso usuário, para podermos fazer isso, dentro da classe `SecurityConfig`, precisamos adicionar o seguinte método e anotar ele como um `@Bean`, para o Spring fazer o gerenciamento dele:
```java
@Bean
public PasswordEncoder passwordEncoder() {
	return new BcryptPasswordEncoder();
}
```
- Agora em nossa `service`, onde estamos fazendo o cadastro do usuário no banco de dados o seguinte:
```java
// Injetamos a classe
	private final PasswordEncoder passwordEncoder;



public User saveUser(User user) {
	String password = user.getPassword();
	user.setPassword(passwordEncoder.encode(password));
	return userRepository.save(user);
}
```
- Agora podemos fazer o endpoint de `login`, para podermos autenticar o nosso usuário.
- Então em nosso `AuthController`, vamos criar outra rota do tipo `POST`, como no exemplo abaixo:
```java
@PostMapping("/login")
public ResponseEntity<String> login(@RequestBody LoginRequest request) {}
```
- Em nosso `LoginRequest`, precisamos do email e da senha:
```java
public record LoginRequest(String email, String password) {}
```
- Agora em nossa entidade `User`, vamos fazer a implementação da interface `UserDetails`, e adicionar os métodos, como no exemplo abaixo:
```java
// Anotações
@Entity
public class User implements UserDetails {
	
	// id
	
	// string name
	
	// string email
	
	// string password
	
	// implementamos todos os métodos da interface
	
}
```
- Agora vamos criar a nossa `AuthService`, e nela vamos fazer a implementação da interface `UserDetailsService`, como no exemplo abaixo:
```java
@Service
public class AuthService implements UserDetailsService {

	private final UserRepository userRepository;
	
	// construtor

	@Override
	public UserDetails loadUserByUsername(String username) throws UsernameNotFoundException {
		userRepository.findByEmail(username);
	}
}
```
- Na interface `UserRepository`, implementamos o método `findByEmail(String email)`, como no exemplo abaixo:
```java
public interface UserRepository extends JpaRepository<User,Long> {
	
	Optional<UserDetails> findUserByEmail(String email);
	
}
```
- Agora em nossa `AuthService`, continuamos a implementação:
```java
@Service
public class AuthService implements UserDetailsService {

	private final UserRepository userRepository;
	
	// construtor

	@Override
	public UserDetails loadUserByUsername(String username) throws UsernameNotFoundException {
		userRepository.findByEmail(username).orElseThrow(() -> new UsernameNotFoundExcepetion("Usuário ou senha inválido"));
	}
}
```
- Voltando para a nossa `controller`vamos continuar a implementação do método `login`
```java
@PostMapping("/login")
public ResponseEntity<String> login(@RequestBody LoginRequest request) {
	UsernamePasswordAuthenticationToken userAndPass = new UsernamePasswordAuthenticationToken(request.email(), request.password());
	
	Authentication authenticate = authenticationManager.authenticate(userAndPass);
	
	User user = (User) authenticate.getPrincipal();
}
```
- ***Lembrando que precisamos fazer a injeção do `AuthenticationManager`;***
- Em nossa `SecurityConfig`, vamos precisar adicionar também o seguinte método:
```java
@Bean
public AuthenticationManager authenticationManager(AuthenticationConfiguration authenticationConfiguration) throws Exception {
	return authenticationConfiguration.getAuthenticationManager();
}
```
- Agora para podermos gerar o *token JWT*, para isso precisamos criar uma classe, que vamos chamar ela de `TokenService`
- Agora dentro do *package* `config`, vamos criar o `TokenService`, e dentro dela vamos fazer o seguinte:
```java
@Component
public class TokenService {
	
	public String generateToken(User user) {
		Algorithm algorithm = Algorithm.HMAC256("");
		
		return JWT.create()
			.sign()
	} 
	
}
```
- Para o `Algorithm.HMAC256()`, precisamos passar uma chave secreta, para fazer isso, vamos em nosso ***`application.yaml`*** e vamos adicionar:
```yaml
movieflix:
	security:
		secret: "palavra-secreta"
```
- Agora voltamos ao nosso `TokenService`e configuramos da seguinte maneira:
```java
@Component
public class TokenService {

	@Value("${movieflix.security.secret}")
	private String secret;
	
	public String generateToken(User user) {
		Algorithm algorithm = Algorithm.HMAC256(secret);
		
		return JWT.create()
			.withSubject(user.getEmail())
			.withClaim("userId", user.getId())
			.withExpiresAt(Instant.now().plusSeconds(86400))
			.withIssuedAt(Instant.now())
			.sign(algorithm)
			
	} 
	
}
```
- Agora voltamos ao nosso `AuthController`e injetamos o nosso `TokenService`
```java
public class AuthController {
	
	// outras injeções
	private final TokenService tokenService;
}
```
- E agora em nosso método de **`login`** fazemos o seguinte:
```java
@PostMapping("/login")
public ResponseEntity<LoginResponse> login(@RequestBody LoginRequest request) {
	UsernamePasswordAuthenticationToken userAndPass = new UsernamePasswordAuthenticationToken(request.email(), request.password());
	
	Authentication authenticate = authenticationManager.authenticate(userAndPass);
	
	User user = (User) authenticate.getPrincipal();
	
	String token = tokenService.generateToken(user);
	
	return ResponseEntity.ok(new LoginResponse(token));
}
```
- Como alteramos o retorno do método para ***`LoginResponse`***, precisamos criar ele, então no *package* de response, vamos criar
```java
public record LoginResponse(String token) {}
```