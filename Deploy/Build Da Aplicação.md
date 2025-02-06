___
- Fazemos o *build* da nossa aplicação para transformar o projeto que está em `Typescript`para `Javascript`.
- Para fazer isso vamos precisar de uma ferramenta, que instalamos usando:
```zsh
npm i tsup -D
```
- Após a instalação, vamos no arquivo `package.json`, e vamos criar um novo `script`:
```json
"build": "tsup src"
```
- E agora para buildar o nosso projeto usamos o comando:
```zsh
npm run build
```
- Após rodar o comando acima, ele vai gerar uma pasta com o nome de `dist`, nesta pasta estará todos os arquivos da aplicação em `Javascript`, mas podemos alterar o nome dessa pasta.
- Para alterar o nome dessa pasta voltamos ao arquivo `package.json`e alterarmos o script para:
```json
"build": "tsup src --out-dir build"
```
- Desta maneira a pasta gerada irá ter o nome de `build`.