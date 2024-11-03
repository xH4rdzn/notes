___
- Como vimos podemos criar [[Funções com Parâmetros|funções com parâmetros]], mas as vezes podemos não precisamos de todos os parâmetros para executar a função.
- Para isso podemos passar parâmetros opcionais, para não dar erro caso não passamos um parâmetro.
- Para fazer com que algum parâmetro fique opcional, seguimos o exemplo:
```c#
public void Teste(int valor1, int valor2 = 7) {}
```
- No exemplo acima, caso não passarmos dois parâmetros quando formos utilizar a função, o valor do segundo parâmetro por padrão vai ser 7, mas caso informamos o valor passado em seu uso, vai sobrescrever o valor padrão.
- ***O PARÂMETRO OPCIONAL DEVE SER O ÚLTIMO PARÂMETRO A SER PASSADO***