___
## Fundamentos

#### JSON - Javascript Object Notation
- É o padrão entre APIs, na maioria das linguagens da programação.
- É usado para trafegar dados.
- Podemos usar para fazer a comunicação entre diversos back-end;
```json
{
	"name": "Igor Coelho",
	"idade": 26,
}
```
#### URL
```text
https://api.meuapp.com/users/32?posts=true
```
- https -> Protocolo
- api -> subdomínio
- meuapp.com -> domínio
- /users -> recurso
- 32 -> parâmetro (Route Params) -> É obrigatório
- ?posts=true -> parâmetro de busca (Query Params/ Search Param) -> Não é obrigatório

#### Métodos HTTP
- `GET` -> Buscar informações
```url
GET localhost:3333/users/1/posts
```
- `POST`-> Criar 
```url
POST localhost:3333/users/1/posts
```
- `PUT`-> Atualizar uma entidade por completo
```url
PUT localhost:3333/posts/1
```
- `PATCH`-> Atualizar uma entidade parcialmente
```url
PATH localhost:3333/posts/1/title
```
- `HEAD` ->  
```url
HEAD localhost:3333/posts/1
```
 
#### Route Param 
- Identificação de recursos
- Obrigatório
```url
localhost:3333/users/1
```
#### Search Param ou Query Param
- Filtrar resultados
- Não é obrigatório
```url
localhost:3333/users/1/posts?search=node
```

#### Request Body
- Dados para criação/atualização de um recurso (obrigatórios ou opcionais)
- São usados em rotas do tipo: `POST, PUT, PATCH`;

#### Headers - Cabeçalhos
- Servem para trafegar metadados, que são informações adicionais que não alteram o resultado/funcionamento.
```header
Header -> accept-language: en
```

#### HTTP Status Code
- Podem começar:
	- 2xx -> Significa que deu certo/sucesso
		- 201 -> created, geralmente usado com método HTTP `POST`
		- 202 -> aceito, mas não garante que realmente deu certo.
		- 204 -> not content, sem retorno
	- 3xx -> Significa redirecionamento
	- 4xx -> Erro do cliente
		- 418 -> I'm a teapot (Eu sou uma bule de chá)
	- 5xx -> Erro do servidor (API)