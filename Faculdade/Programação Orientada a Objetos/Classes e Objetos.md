___
### Classe
- Classificação de objetos
- Abstração para modelar o mundo
- Aproximação da lógica da programação com a da linguagem falada
```java
public class Aluno {}
```
- Para fazer a instância dessa classe, para transformar em um objeto concreto usamos o operador ***`new`***
```java
Aluno a = new Aluno();
```
### Atributos
- Características do objeto
- Do que o objeto é composto
- São declarados como variáveis
```java
public class Aluno {
	
	// Atributos
	int matricula;
	String nome;
	String cpf;

}
```
### Métodos
- O que o objeto faz
```java
void info() {
	// Código
}
```
### Estado
- Em que situação o objeto está

## Padrões e modificador Static
- Para definir classes, usamos o padrão de nomenclatura de CamelCase, como é demonstrado no exemplo abaixo:
```java
public class MinhaClasse {}
```
- Para pacotes, eles são descritos inteiramente em letras minúsculas
```java
package meupacote;
```
- Para Métodos, atributos e variáveis, inicia com letra minúscula e segue o camelCase;
```java
void mostrarInformacoes() {}

String nomeCompleto;
```
- Para constantes, inteiramente com letras maiúsculas separadas por *underline*
```java
String final NOME_COMPLETO = "IGOR RODRIGUES COELHO";
```

#### Static
- Método *static*
	- Método é executado sem estar associado a uma instância
- Atributo *static*
	- O atributo se torna global. É acessada a mesma variável, mesma posição de memória, por todas as instâncias