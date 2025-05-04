___
- Uma das maiores dúvidas quando estamos fazendo testes é, será que testamos a nossa aplicação o suficiente ?
- Para isso temos uma funcionalidade chamada de *coverage*.
- Para isso vamos nosso arquivo `package.json`e vamos criar um novo script:
```json
"test:coverage": "vitest run --coverage"
```
- Agora executamos o comando:
```zsh
npm run test:coverage
```
- Ao rodar esse comando será gerado uma pasta com o nome de `coverage`em nossa aplicação, devemos por essa pasta no `.gitignore`, e dentro dela irá gerar um arquivo `index.html`ao abrirmos vamos ver uma tela onde mostra todos os arquivos que foram testados da nossa aplicação.