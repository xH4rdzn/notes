___
- Todas as aplicações que vamos fazer vão usar banco de dados, e a maioria das aplicações usam banco de dados relacionais.
- Então vamos usar o banco `sqlite`, em nossa aplicação, pois com ele não precisamos utilizar ferramentas como o `docker`, pois todos os arquivos do `sqlite`são salvos em arquivos físicos, sem precisar fazer a instalação de qualquer ferramente no seu computador.
- Após descobrir qual banco de dados vamos utilizar, precisamos definir qual a estratégia que vamos utilizar para conectar nossa aplicação com o banco de dados, e temos 3 estratégias para seguir que são:
- ***Drivers Nativos*** -> que são a maneira menos abstrata possível, ou seja precisamos escrever exatamente a `query`que queremos que o banco de dados execute.
- ***Querys Builder*** -> é a maneira que não precisamos entender muito de `sql`, mas precisamos saber pelo menos a linguagem de programação que estamos utilizando;
- ***ORM*** -> é a terceira maneira, no qual relacionamos objetos com tabelas do banco de dados e quase não utilizamos `sql`;
