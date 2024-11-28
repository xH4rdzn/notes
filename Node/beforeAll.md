___
- Existem cenários em que alguma coisa precisa estar disponível antes de executar os testes, para isso existe o método `beforeAll`, com esse método conseguimos executar uma função antes dos testes;
```ts
beforeAll(() => {
	sumResult = 10
})
```
*O exemplo acima é bem simples, mas podemos ter coisas mais complexas, como conexão com banco de dados, mudar variáveis ambiente, por exemplo*;