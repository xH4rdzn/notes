___
- Como [[Criando o Modelo das Tabelas|definimos]] as tabelas, agora precisamos rodar uma `migration`, para que essas tabelas sejam criadas no banco de dados;
- Para fazer a `migration`, vamos utilizar o comando:
```zsh
npx prisma migrate dev
```
- Ao rodar esse comando, precisamos dar um nome para essa `migration`, após isso é só esperarmos terminar.
- Após terminar podemos utilizar ferramentas como o `Beekeeper`, para fazer a visualização, ou podemos usar o `Prisma Studio`, que é da ferramenta que estamos utilizando, para executar o `Prisma Studio`, rodamos o comando:
```zsh
npx prisma studio
```
