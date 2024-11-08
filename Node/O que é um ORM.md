___
- *ORM (Object Relational Mapper)* é uma ferramenta que facilita o trabalho com banco de dados em aplicações, permitindo que você interaja com o banco sem escrever consultas SQL diretamente.
- Com o *ORM*, você manipula tabelas e dados do banco como se fossem objetos com a linguagem de programação, simplificando a leitura, escrita e manutenção do código. Ele também cuida da conversão dos dados entre o banco de dados relacional(tabelas) e os objetos no código.
#### Vantagens
- Menos código SQL manual
- Facilita a manutenção
- Compatível com múltiplos bancos de dados
#### ORM x Query Builder
- A principal diferença entre um *ORM* e um *Query Builder*, é o nível de abstração e como eles interagem com o banco de dados.
- *ORM* -> converte tabelas do banco de dados em objetos da linguagem de programação. Você usa objetos e o ORM faz o SQL para você.
- *Query Builder* -> ajuda a criar consultas SQL usando código, sem escrever SQL diretamente. Dá mais controle, mas exige mais trabalho.