___
## Conceitos, definições e modelos

#### Dados versus informação
- A reunião de dados relacionados ao mesmo assunto transforma-se em informação

#### Banco de dados
- Sistema computadorizado de armazenamento de registros, cujo objetivo é armazenar informações e permitir ao usuário buscá-las e atualizá-las quando necessários
- Exemplos:
	- Sistema de delivery
	- Sistema acadêmico

#### Modelos de banco de dados
- É a forma como os banco de dados são construídos conceitualmente
- Modelos:
	- Modelo hierárquico
	- Modelo de rede
	- Modelo orientado a objetos
	- Modelo NoSQL (não relacional)
	- Modelo Relacional

## Sistema Gerenciador de Banco de dados (SGBD) e aplicações de banco de dados

- Sistema de gerenciador de banco de dados(SGBD) é a interface entre os dados de baixo nível, armazenados em um banco de dados, e os usuários e aplicações que desejam acessar e manipular esses dados.
- Objetivos:
	- Abstração de dados
	- Independência de dados em relação às aplicações
- Exemplos:
	- DB2, Microsoft SQL Server, Oracle, MySQL, PostgreSQL, entre outros

#### Características de um SGBD
- Controle de redundância
- Compartilhamento dos dados e concorrência
- Controle de acesso
- Controle de transações
- Possibilidade de múltiplas interfaces
- Restrições de integridade
- Backup e recuperação de dados
- Independência de dados
- Eliminação de inconsistências
- Padronização dos dados

#### Pontos de atenção em um SGBD
- Dispositivos de controle adequados
- Integridade das informações
- Levantamento de dados
- Administração do banco de dados

#### Administrador de Banco de dados (DBA)
- Definição do banco de dados
- Estrutura de armazenamento e definição de acesso aos dados
- Esquema físico e organização dos dados
- Controle de acesso dos usuários
- Cuidar da integridade dos dados
- Acompanhar o desempenho do banco de dados
- Atividades de manutenção e backup

## Modelagem de dados
- Consiste no levantamento e análise de dados sobre as informações e como relacionam-se entre si, desenvolvendo um modelo que representa a realidade de um cenário.
- Modelos básicos: *conceitual, lógico e físico*
- A análise, juntamente com os modelos, produzem o projeto de banco de dados

## Modelo Entidade-Relacionamento (*MER*)

#### Modelo de dados conceitual
- Esse modelo abrange:
	- Visão geral do negócio (regras)
	- Comunicação entre usuários e desenvolvedores
	- Definição das entidades e principais campos
	- Independente da implementação e do SGBD
	- Descrição mais abstrata do banco de dados
	- Aplicação da técnica do MER

#### Modelo Entidade-Relacionamento (MER)
- Abstração de alto nível - visão do usuário
- É desenvolvido com base em três elementos:
	- Entidade -> objeto do mundo real
	- Campo -> características particulares de cada objeto
	- Relacionamento -> relação entre entidades
![[Pasted image 20260223194154.png]]
#### Entidade
- Baseada na estrutura da chave primária e no grau de dependência
- Pode ser representada como:
	- Entidade fundamental -> presença de uma chave primária simples
	- Entidade associativa -> baseia-se em relações n:n envolvendo várias entidades
	- Entidade fraca -> depende de outra entidade para existir (dependência existencial)

#### Instância de uma entidade
- Informações armazenadas nos campos de uma entidade
- Exemplo:

|     Pessoa      |                |                          |
| :-------------: | :------------: | :----------------------: |
|      nome       |      CPF       |         endereco         |
|  Zanana Silva   | 123.456.789.00 |   Rua das flores, 999    |
| Wilquison Souza | 789.123.456.11 | Avenida 7 de setembro, 1 |
#### Campo
- Características de uma entidade
- Tipos de campos:
	- Obrigatório
	- Opcional ou nulo
	- Simples ou atômico
	- Composto
	- Monovalorado
	- Multivalorado
	- Derivado
- Domínio: possível valor definido para determinado campo
- Exemplo: salário, valor numérico positivo com duas casas decimais
#### Chaves de um campo
- Identificam cada instância separadamente em um banco de dados
- Garantem o relacionamento entre as entidades
- Tipos:
	- Chave primária (PK -> Primary Key)
		- Chave primária não natural
	- Chave estrangeira (FK -> Foreign Key)

#### Relacionamento ou associação
- Comunicação entre as entidades
- Tipos especiais:
	- Recursivo ou atorrelacionamento
	- Especialização e generalização
![[Pasted image 20260223195555.png]]

## Cardinalidade
- Determina a relação entre as entidades
- Com base nas instâncias do objeto
- Formas:
	- Um para um (1:1)
	- Um para muitos (1:n) / muitos para um (n:1)
	- Muitos para muitos (n:n) / (n:m)
	- Máxima e mínima
#### Cardinalidade um para um (1:1)
- Relacionamento exclusivo
- **Uma** instância está associada a ***uma*** instância de outra entidade.
![[Pasted image 20260223195938.png]]
#### Cardinalidade (1:1) - chave estrangeira
- A entidade que recebe a chave estrangeira fica a critério do projetista
- Existência opcional

#### Cardinalidade um para muitos (1:n)
- ***Uma*** entidade associada a *várias* instâncias de outra entidade. O inverso não ocorre, em que *uma* entidade pode estar associada a *uma* instância
![[Pasted image 20260223202830.png]]
#### Cardinalidade (1:n) - c have estrangeira
- A chave estrangeira é sempre declarada no lado da entidade que recebe muitos (n)

#### Cardinalidade muitos para muitos (n:n)
- ***Várias*** instâncias de uma entidade associada a *várias* instâncias de outra entidade.
![[Pasted image 20260223203042.png]]

#### Cardinalidade mínima e máxima
![[Pasted image 20260223203554.png]]