___
- No `Insomnia`, que usamos para testar as nossas requisições, podemos deixar atualização de token automática da seguinte maneira:
1. Na parte `Auth`da nossa requisição que queremos autorizar, colocamos o `Bearer Token`;
2. Mudamos o valor de `TOKEN`, para:
```text
response
```
3. Escolhemos a opção com `Body Attribute`;
4. Após isso clicamos em cima do valor que irá ficar vermelho, e no campo `Request`escolhemos a requisição onde é criado o nosso `Token`;
5. No campo `Filter`, passamos o seguinte valor:
```text
$.token
```