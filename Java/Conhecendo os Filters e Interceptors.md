___
### Conhecendo os Filters

#### O que são os Filters ?
- São componentes do **ecossistema de Servlet** que atuam como intermediário das requisições http no contexto de WebServer.
- Eles operam no nível mais baixo, próximo ao WebServer. Com isso, não possui acesso ao contexto do Spring.
- Ideal para ***`cross-cutting concerns`***, ou seja, tarefas que se aplicam para toda a sua aplicação
- Exemplos de uso: Manipulação de cabeçalhos HTTP, logging, auditoria, compressão de respostas, etc.

### Conhecendo os Interceptors

#### O que são os Interceptors ?
- São componentes do **ecossistema do Spring** que atuam como intermediário das requisições http.
- Eles tem acesso aos dados da requisição antes mesmo que ela chegue na controladora.
- Eles operam no nível mais alto. Os *interceptors* tem acesso ao contexto de requisição do Spring
- Ideal para pré e pós processamento da requisição, antes que ela chegue na controladora.
- Exemplos de uso: Medição de performance, validação de dados, alteraçõa de headers HTTP, etc.

### Filters vs Interceptors
- `Filters` e `Interceptors` são bem parecidos, a diferença principal entre eles é o contexto em que atuam.