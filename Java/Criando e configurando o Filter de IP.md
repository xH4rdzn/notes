___
### Criando um filter (ipFilter)
- Para isso vamos criar um *package* que vamos chamar ele de `filter` e dentro desse pacote, vamos criar o nosso filter
```java
@Component
public class IpFilter extends HttpFilter {
	
	@Override
	protected void doFilter(HttpServletRequest request, HttpServletResponse response, FilterChain chain) throws IOEception, ServletException {
	
		var ipAddress =	request.getRemoteAddr();
		
		response.setHeader("x-user-ip", ipAddress);
	
		chain.doFilter(request, response);
	}
	
}
```
- E agora para podermos registrar esse novo `filter`, dentro do *package* `filter`, vamos criar outra classe com o nome de `FilterConfig`, e nela vamos fazer:
```java
@Configuration
public class FilterConfig {

	private final IpFilter ipFilter;
	
	public FilterConfing(IpFilter ipFilter) {
		this.ipFilter = ipFilter;
	}
	
	@Bean
	public FilterRegistrationBean<IpFilter> filterFilterRegistrationBean() {
	
		var registrationBean = new FilterRegistrationBean<IpFilter>();
		
		registrationBean.setFilter(ipFilter);
		registrationBean.setOrder(0);
		
		return registrationBean;
	
	}

}
```
- em ***`setFilter`***, colocamos o filtro que desejamos registrar;
- Em ***`setOrder`***, definimos a ordem de execução desses filtros, onde 0 seria o primeiro;
- Em ***`setUrlPatterns`***, caso não desejamos executar esse filtro em todas as rotas da nossa aplicação, aplicamos um conjunto de rotas ou rotas específicas que desejamos executar esse filtro;

### Explorando as possibilidades de um Filter
- Com o `filter`, podemos desabilitar a nossa aplicação por completo, para não receber mais requisições, para isso podemos simplesmente comentar a linha como no exemplo abaixo:
```java
@Component
public class IpFilter extends HttpFilter {
	
	@Override
	protected void doFilter(HttpServletRequest request, HttpServletResponse response, FilterChain chain) throws IOEception, ServletException {
	
		var ipAddress =	request.getRemoteAddr();
		
		response.setHeader("x-user-ip", ipAddress);
		response.setStatus(503);
	
		// chain.doFilter(request, response);
	}
	
}
```

### Passando os atributos para as próximas requisições
- Para podermos fazer isso, adicionamos o `setAttribute`, como é demonstrado no exemplo abaixo:
```java
@Component
public class IpFilter extends HttpFilter {
	
	@Override
	protected void doFilter(HttpServletRequest request, HttpServletResponse response, FilterChain chain) throws IOEception, ServletException {
	
		var ipAddress =	request.getRemoteAddr();
		
		request.setAttribute("x-user-ip", ipAddress);
		response.setHeader("x-user-ip", ipAddress);
		
		chain.doFilter(request, response);
	}
	
}
```