___
- Os parâmetros nomeados ou `query params`, não são obrigatórios, e podem ser passados para a `url` da seguinte maneira:
```text
/products?page=1&limit=10
```
- E agora para recuperarmos esses valores, fazemos da seguinte maneira:
```ts
const { page, limit } = request.query
```
- Agora podemos usar no nosso código;
