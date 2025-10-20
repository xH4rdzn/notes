___
### Banco de Dados Relacional
- Os bancos de dados relacionais, também chamados de bancos SQL possuem uma estrutura hierárquica que permite a organização das suas informações em tabelas, contendo linhas e colunas.

| ID  | CPF          | NOME           | TELEFONE   | NASCIMENTO |
| --- | ------------ | -------------- | ---------- | ---------- |
| 1   | 111111111111 | PEDRO HENRIQUE | 2166194919 | 1992-08-28 |
| 2   | 222222222222 | ANA LUISA      | 9191919491 | 1993-04-01 |
| 3   | 33333333333  | VANESSA        | 9499119191 | 1990-08-25 |
| 4   | 44444444444  | MARIO          | 9191949156 | 1993-01-30 |

### Banco de dados Não Relacional
- É muito utilizado pela sua alta performance e por manter todos os registros em uma única estrutura de dados. Portanto, não é necessário criar um sistema de relacionamento como é feito nos bancos de dados relacionais. Como as informações não estão associadas entre si, é mais fácil fazer alterações e exclusões no conteúdo.
- Existem diversos tipos de banco de dados não relacional, eles são categorizadas pela sua maneira de armazenamento de dados. Os dois tipos mais utilizados de bancos NoSQL são:
	- Chave-Valor
	- Baseado em documentos

### NoSQL: Baseado em documentos
- Os bancos não relacional baseado  em documentos armazenam seus dados de forma semelhante aos objetos ***JSON***. Eles guardam todas as informações para um determinado objeto em uma única instância no banco de dados e cada objeto armazenado pode ser diferente de todos os outros.
- Normalmente, possuem poderosas linguagens para consultas e podem ser facilmente escalados de forma horizontal, acomodando uma grande quantidade de informações.

### SQL x NoSQL

|                | SQL                                 | NOSQL                                                      |
| -------------- | ----------------------------------- | ---------------------------------------------------------- |
| Histórico      | Foco na redução de dados duplicados | Foco em escalabilidade e mudança rápida de desenvolvimento |
| Armazenamento  | Tabelas com linhas e colunas        | Documentos JSON, Chave-Valor                               |
| Esquemas       | Rígido                              | Flexível                                                   |
| Esscalonamento | Vertical                            | Horizontal                                                 |
| Exemplos       | Oracle, MySQL, PostgreSQL           | MongoDB, DynamoDB, Redis                                   |
