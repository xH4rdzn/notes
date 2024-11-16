___
- São parâmetros que vão no corpo da requisição, usamos ele geralmente com o método HTPP `POST`;
- Para recuperar os dados do corpo da requisição fazemos da seguinte maneira:
```java
@PostMapping("/exemploBodyParams")
public String metodoBodyParams(@RequestBody String username) {
	return "Corpo da requisição: " + username;
}
```
- Para recebermos um objeto inteiro no corpo da requisição podemos usar o `record`, que são básicamente classes que não precisam de métodos e nem atributos e o passamos para o método da seguinte maneira:
```java
// Record
record User(String username, String email){}
```
- Passando para o método
```java
@PostMapping("/exemplo")
public String metodoBodyParams(@RequestBody User user) {
	return "Os Body Params são: " + user.username + " " + user.email;
}
```