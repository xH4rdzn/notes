___
- Agora que [[Criando a nossa primeira classe|criamos a nossa primeira classe]] que é um modelo para criar um objeto, vamos instanciar esse objeto.
- Em outras palavras é criar um objeto do tipo da classe
- Para instanciar um novo objeto usamos a keyword `new`, mas precisamos de uma maneira para se referenciar para aquele objeto em especifico, então para instanciar um objeto seguimos o exemplo abaixo:
```java
Conta primeiraConta = new Conta();
```
`Conta é a classe que criamos na nota:` [[Criando a nossa primeira classe]]
- Agora que instanciamos um objeto do tipo conta, podemos atribuir valores para os atributos definidos na classe.
- Para fazer isso usamos a notação `.`, a partir da variável instanciada. Como no exemplo abaixo:
```java
Conta primeiraConta = new Conta();
primeiraConta.saldo = 1525.40;
primeiraConta.agencia = 1;
primeiraConta.numero = 100;
primeiraConta.titular = "Igor Coelho";
```
- **Nota-se que usamos o nome da variável que faz referência ao objeto instanciado, e o nome dos atributos que criamos na classe.**

