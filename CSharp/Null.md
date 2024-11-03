___
- Usamos o `null`, para valores que podem ser informados ou não, `null` é nulo, ou seja que não foi informado.
- Porém se passarmos `null` para qualquer tipo de variável vai dar erro, para resolver esse problema passamos `?` . Como no exemplo abaixo:
```c#
int? idade = null;
```
- Quando uma variável é opcional ganhamos os métodos `HasValue` e `Value`;
- `Value`-> retorna o valor da variável caso haja.
- `HasValue`-> retorna um booleano se tem um valor ou não.