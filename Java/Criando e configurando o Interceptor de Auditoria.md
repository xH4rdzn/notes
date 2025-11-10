___
### Criando o Interceptor de Auditoria
- Para criar um ***`interceptor`***, vamos criar o *package interceptors*, e dentro dele vamos criar o `AuditInterceptor`, e nele implementamos o `HandlerInterceptor`, como no exemplo abaixo:
```java
public class AuditInterceptor implements HandlerInterceptor {}
```
- Como implementamos uma *interface*, precisamos sobrescrever os métodos contidos nela.
- Que são os métodos `preHandle`, `postHandle` e o `afterCompletion`;
- O método `preHandle`, vai executar antes deles chegarem em nossa controller. Quando retornamos um `boolean`nesse método é um indicativo de que queremos dizer que a requisição siga(*true*) ou que ela fique bloqueada(*false*);
- O método `postHandle`, vai executar depois da execução da nossa controller;
- O método `afterCompletion`é executado depois do método `postHandle`;
```java
public class AuditInterceptor implements HandlerInterceptor {

	private final Logger logger = new LoggerFactory.getLogger(AuditInterceptor.class);
	
	
	@Override
	public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
	
		logger.info("pre-handle");
		return true;
	
	}
	
	@Override
	public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Excepetion {
	
		logger.info("post-handle");
	
	}
	
	@Override
	public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception {
		
		logger.info("after-completion");
		
	}

}
```

### Registrando um Interceptor no Spring Boot
- Para registrar esse *interceptor*, precisamos passar a anotação de `@Component`na nossa classe
```java
@Component
public class AuditInterceptor implements HandlerInterceptor {}
```
- Dentro do *package interceptors*, vamos criar a classe `InterceptorConfig` e nele vamos fazer o seguinte:
```java
@Configuration
public class InterceptorConfig implements WebMvcConfigurer {
	
	private final AuditInterceptor auditInterceptor;
	
	public InterceptorConfig(AuditInterceptor auditInterceptor) {
		this.auditInterceptor = auditInterceptor;
	}
	
	@Override
	public void addInterceptors(InterceptorRegistry registry) {
		
		registry.addInterceptor(auditInterceptor)
		.order(0);
	}
	
	
}
```
- Como vimos em [[Criando e configurando o Filter de IP|no registro de filters]], podemos também adicionar `order`e `addPathPatterns`, para podermos executar em rotas específicas. Se não adicionarmos nada ele vai executar para todas as rotas da nossa aplicação.
- Agora podemos voltar ao nosso interceptor e adicionar:
```java
public class AuditInterceptor implements HandlerInterceptor {

	private final Logger logger = new LoggerFactory.getLogger(AuditInterceptor.class);
	
	
	@Override
	public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
	
	
		return true;
	
	}
	
	@Override
	public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Excepetion {
	
	
	}
	
	@Override
	public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception {
		
		logger.info("Audit - Método: {}, Url: {}, StatusCode: {}, IpAddress: {}",
		request.getMethod(),
		request.getRequestURI(),
		response.getStatus(),
		request.getAttribute("x-user-ip")
		
	}

}
```
