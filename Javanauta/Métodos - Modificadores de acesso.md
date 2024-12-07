___
- Função (método): É um bloco de código que realiza uma tarefa específica, que pode ser reutilizado em **diferentes partes do programa**.
- Método: Termo usado em programação orientada a objetos que se refere a funções associadas a uma classe ou objeto.
- Sintaxe de Definição de Métodos:
```java
	modificadorDeAcesso tipoDeRetorno nomeDoMétodo (parâmetros) {}
```
- Como por exemplo:
```java
	public String digaOla(String nome) {
		return "Olá " + nome;
	}
```
- Os modificadores de acesso podem ser:
	- **public**-> Acessível de qualquer lugar do nosso código;
	- **private**-> Acessível apenas dentro da classe onde foi criado;
	- **protected**-> Acessível dentro do mesmo pacote ou subclasses;
- Esses modificadores de acesso, podem ser utilizados nos atributos também, podemos ver em [[]];
