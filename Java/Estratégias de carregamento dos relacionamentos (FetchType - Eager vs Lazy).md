___

### Quais são as estratégias ?
- As estratégias de carregamento (*FetchType*)dos relacionamentos determinam como e quando as associações entre entidades são carregadas.
#### FetchType.LAZY
- Carrega a associação somente quando é acessada pela primeira vez.
	- Melhora a performance ao evitar carregamento desnecessário de dados.

#### FetchType.EAGER
- Carrega a associação imediatamente junto com a entidade principal. Útil quando é necessário acessar a associação frequentemente
	- Pode impactar a performance se a associação for grande ou complexa.

### Lazy
- Carrega a associação somente quando é acessada pela primeira vez.
#### Vantagens
- Na maioria dos casos temos uma melhora na performance ao evitar carregamento desnecessário de dados.
#### Desavantagens
- Caso você precise da informação, poderemos ter queries mal otimizadas, pois iremos mais vezes ao banco de dados.

### Eager
- Carrega a associação imediatamente junto com a entidade principal. Útil quando é necessário acessar a associação frequentemente
#### Vantagens
- Diminuímos a quantidade de vezes de idas ao banco de dados otimizando o processamento.
- Ideal para dados frequentemente consultados
#### Desvantagens
- Pode impactar a performance se a associação for grande ou complexa