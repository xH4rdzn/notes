___
- Podemos também usar a UI do `vitest`, onde podemos executar os nossos testes de forma visual.
- Mas para isso precisamos instalar uma biblioteca, para isso usamos o comando:
```zsh
npm i @vitest/ui -D
```
- E agora nosso arquivo `package.json`, vamos criar um novo `script`:
```json
"test:ui": "vitest --ui"
```
- Agora rodamos o comando:
```zsh
npm run test:ui
```
- E irá abrir uma página com nossos testes, onde podemos executar e fazer a verificação de quais módulos faz uso e etc.