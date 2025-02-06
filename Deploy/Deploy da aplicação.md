___
- Após fazermos o deploy do [[Criando o banco de dados|banco de dados]], voltamos ao *dashboard* e escolhemos a opção de **Web Service**, assim ele vai buscar todos os repositórios do *Github*, para podermos fazer o deploy
- Após ele se conectar, precisamos fazer algumas configurações;
- Podemos alterar o nome;
- Mas a principal é o ***Build Command***, nesta parte alteramos o código para buildar o nosso projeto e o iniciar, então nosso comando fica mais ou menos como no exemplo abaixo:
```zsh
npm install && npm run build && npx prisma migrate deploy
```
- O `npm install`, vai instalar as dependencias do projeto;
- O `npm run build`, vai buildar o nosso projeto de `Typescript` para `Javascript`;
- O `npx prisma migrate deploy`, vai gerar nossas tabelas no banco de dados;
- Agora em **Start Command**, precisamos passar o comando que vai inicializar a nossa aplicação, como configurado no projeto vamos usar o comando:
```zsh
npm start
```
- Agora precisamos configurar as **Environment Variables**, que são as variáveis de ambiente;
- Nessa parte adicionamos as variáveis que tem no nosso arquivo `.env`;
- Precisamos pegar a *url* do banco de dados para poder fazer a conexão com a aplicação.
- Após isso basta apenas fazer o deploy e aguardar;