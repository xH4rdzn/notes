___
- Como já configuramos o nosso `login`[[Spring Security|anteriormente]], agora precisamos configurar para poder fazer autenticação.
- Para isso em nossa classe `SecurityConfig`, que está dentro do *package* `config`, vamos fazer as seguintes adições:
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
		.addFilterBefore(securityFilter, UsernamePasswordAuthenticationFilter.class)
		.build();
		
	}
}
```
- E agora dento desse *package* ainda, vamos criar a classe `SecurityFilter`, como no exemplo abaixo:
```java
@Component
public class SecurityFilter extends OncePerRequestFilter{
	
	private final TokenService tokenService;
	
	@Override
	protected void doFilterInternal(HttpServletRequest request, HttpServletResponse response, FilterChain filterChain) {
		String authorizationHeader = request.getHeader("Authorization");
		if(Strings.isNotEmpty(authorizationHeader) && authorizationHeader.startsWith("Bearer ")) {
			String token = authorizationHeader.substring("Bearer".length());
			
			tokenService.validate(token);
			
			
			
			filterChain.doFilter(request, response);
		} else {
			filterChain.doFilter(request, response);
		}
		
	}
	
}
```
- Agora em nossa `TokenService`, vamos criar o método `validate`, para poder validar o nosso token, como no exemplo abaixo:
```java
public void validate(String token) {
	Algorithm algorithm = Algorithm.HMAC256(secret);
	
	DecodedJWT verify = JWT.require(algorithm)
		.build()
		.verify(token);
		
	verify.getSubject()	
}
```
- Como agora conseguimos várias informações do nosso usuário, vamos criar o *record* `JWTUserData`, para retornar um objeto:
```java
@Builder
public record JWTUserDate(Long id, String name, String email) {}
```
- E agora no nosso `TokenService`, vamos poder retornar agora esse *record*
```java
public Optional<JWTUserData> validate(String token) {
	try {
		Algorithm algorithm = Algorithm.HMAC256(secret);
	
		DecodedJWT jwt = JWT.require(algorithm)
		.build()
		.verify(token);
		
		return Optional.of(JWTUserData
		.builder()
		.id(jwt.getClaim("userId").asLong())
		.name(jwt.getClaim("name").asString())
		.email(jwt.getSubject())
		.build());
	} catch (JWTVerificationException ex) {
		return Optional.empty();
	}	
}
```
- Agora em nosso `SecurityFilter`, vamos fazer o seguinte:
```java
@Component
public class SecurityFilter extends OncePerRequestFilter{
	
	private final TokenService tokenService;
	
	@Override
	protected void doFilterInternal(HttpServletRequest request, HttpServletResponse response, FilterChain filterChain) {
		String authorizationHeader = request.getHeader("Authorization");
		if(Strings.isNotEmpty(authorizationHeader) && authorizationHeader.startsWith("Bearer ")) {
			String token = authorizationHeader.substring("Bearer".length());
			
			Optional<JWTUserData> optJwtUserData = tokenService.validate(token);
			
			if(optJwtUserData.isPresent()) {
				JWTUserData jwtUserData = optJwtUserData.get();
				
				UsernamePasswordAuthenticationToken authenticationToken = new UsernamePasswordAuthenticationToken(jwtUserData, null, null);
			SecurityContextHolder.getContext().setAuthentication(authenticationToken);	
			}
			
			
			filterChain.doFilter(request, response);
		} else {
			filterChain.doFilter(request, response);
		}
		
	}
	
}
```