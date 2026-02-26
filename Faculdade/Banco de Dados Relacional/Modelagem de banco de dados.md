___
## Modelo lógico ou relacional
- Baseado na teoria dos conjuntos (álgebra relacional)
- Dados são estruturados em tabelas (Sistema Gerenciador de Banco de dados - SGBD - específico)
- Refinado pelo processo de normalização
- Base para a criação do modelo físico (banco de dados)
![[Pasted image 20260225163850.png]]
#### Álgebra relacional
- Linguagem de consulta formal
- Dados são representados como relações matemáticas
- Operadores relacionais: unários, binários, derivados e especiais.
![[Pasted image 20260225200552.png]]
#### Restrições de integridade
- Integridade referencial
- Restrição de unicidade
- Restrição de atributos e padrões
- Integridade de chave

## Normalização
- Processo de refinamento aplicado ao modelo lógico
- Benefícios:
	- Minimizar redundâncias e inconsistências
	- Reduzir o tamanho físico do banco de dados
	- Melhorar a manipulação com o banco de dados
- Formas Normais (*FNs*)
##### Primeira Forma Normal - 1FN
- Regras:
	- Cada tupla de dados deve possuir um identificador único (chave primária)
	- Cada tupla de dados deve conter apenas dados atômicos (não repetidos)
![[Pasted image 20260225205727.png]]
![[Pasted image 20260225205757.png]]
##### Segunda Forma Normal - 2FN
- Regras:
	- Em conformidade com a 1FN
	- Ausência de atributos dependentes de parte da chave primária (chave composta)
![[Pasted image 20260225210444.png]]
##### Terceira Forma Normal - 3FN
- Rgras:
	- Em conformidade com a 2FN
	- Ausência de atributo dependente de outros atributos que não sejam chaves na relação.
![[Pasted image 20260225210650.png]]

## Modelo Físico
- Implementação propriamente dita do banco de dados
- Considera as limitações do SGBD escolhido
- Criação das restrições
- Resultado - modelo bem estruturado:
	- Dados com melhor qualidade
	- Menos complexidade nas atualizações e manutenção no banco de dados
#### Modelo Físico - exemplo simples
```sql
create table aluno (
	codigo Integer,
	nome varchar(100),
	endereco varchar(100),
	cidade_codigo integer
);

create table cidade (
	codigo Integer,
	descricao varchar(100),
	uf char(02)
);
```
#### Modelo Físico - versão mais completa
```sql
CREATE TABLE cidade (
	id INTEGER NOT NULL AUTO_INCREMENT,
	estado_id INTEGER NOT NULL,
	descricao varchar(150) NULL,
	PRIMARY KEY(id),
	FOREIGN KEY(estado_id) REFERENCES estado(id) ON DELETE NO ACTION ON UPDATE NO ACTION
);
```
![[Pasted image 20260225211549.png]]
#### Evolução do projeto de banco de dados
![[Pasted image 20260225211702.png]]
#### Terminologia
![[Pasted image 20260225211737.png]]
## Schema/Modelo

#### Modelo Dimensional
- Implementação em banco de dados relacionais
- Objetivo: rapidez na recuperação dos dados
- Desenvolvimento para *Data Warehouse* e *Datamart*
- Dois pilares: **`tabela fato`** e **`tabela dimensão`**
![[Pasted image 20260225212638.png]]
#### Modelo dimensional - fato versus dimensão
- Tabela dimensão:
	- Classificação das medidas que descrevem os fatos
	- Exemplo: nome da cidade para visualizar o valor das vendas
- Tabela fato:
	- Armazena as medidas que serão analisadas
	- Exemplos: valor das vendas
#### Modelos
![[Pasted image 20260225212854.png]]
## Structured Query Language - SQL Linguagem de Consulta Estruturada
- Responsável por toda e qualquer operação em um banco de dados.
- Por meio do SQL (criado pela IBM), diferentes aplicações acessam um banco de dados
- Existem variações do SQL: Oracle, Microsoft, entre outros
#### SQL - dialetos
- As empresas que desenvolvem o SQL criam uma linguagem própria para desenvolvimento de códigos mais avançados
- Essas linguagens são conhecidos como *`dialetos`*
- Exemplo:
	- *`PL/SQL`* é a linguagem do Oracle e MySQL
	- *`Transact-SQL (T-SQL)`*: Microsfot e Sybase
	- *`SQL/PL`*: DB2 da IBM entre outras
- Atualizações:
	- Inclusão dos tipos booleanos (verdadeiro/falso)
	- *`Savepoint`* para transações
	- Comando `merge`
	- Campos autoincrementos
	- Suporte ao *XML* e extensões *JSON*
#### SQL - Categorias
![[Pasted image 20260225214215.png]]
#### SQL - Query/Script
- Linha ou bloco de instruções SQL que serão executados por um SGBD
- Todo comando na *query* deve ser finalizado com ponto e vírgula(;)
![[Pasted image 20260225214543.png]]