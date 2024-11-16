___
- Para passarmos o `Path Params`, no endereço da rota passamos entre `{}`, como no exemplo abaixo que vamos passar o `id`, para a rota e recuperarmos no método;
```java
@GetMapping("/exemplo/{id}")
public String metodo(@PathVariable String id) {}
```
- Nota-se que no `@GetMapping`, passamos o parâmetro de rota entre `{}`
- E no método para poder recuperar esse parâmetro usamos a  anotação `@PathVariable`;
- Caso o parâmetro da rota for igual ao parâmetro que passamos no método podemos fazer igual ao exemplo acima, caso não for, fazemos igual ao exemplo abaixo:
```java
@GetMapping("/exemplo/{id}")
public String metodo(@PathVariable(name = "id") String id) {}
```
- E agora podemos usar esse parâmetro no método da rota:
```java
@GetMapping("/exemplo/{id}")
public String metodo(@PathVariable(name = "id") String id) {
	return "O parâmetro é: " + id;
}
```
- O `Path Params`, fazem parte da rota, então eles são obrigatórios; 

##### Query Params
- Os `Query Params`, diferente do `Path Params`, não são obrigatórios, e o recuperamos esses parâmetros da seguinte maneira:
```java
@GetMapping("/exemploQueryParams")
public String metodoComQueryParams(@RequestParam String id) {
	return "O parâmetro é: " + id;
}
```
- Para recuperar os `Query Params`, usamos o `@RequestParam`
- Os `Query Params`, são passados na URL da seguinte maneira:
```text
localhost:8080/controller/exemploQueryParams?id=189&nome=Igor
```
- Passamos o primeiro parâmetro com `?`, o nome do primeiro parâmetro e seu valor;
- Para passarmos mais valores usamos `&`, o nome do parâmetro e seu valor;
- Para podermos recuperar vários parâmetros de uma vez usamos um `Map`, que vai recuperar a `chave-valor`, como no exemplo abaixo:
```java
@GetMapping("/exemploQueryParams")
public String metodoComQueryParams(@RequestParam Map<String, String> allParams) {
	return "Os parâmetros são: " + allParams.entrySet();
}
```