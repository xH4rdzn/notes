___
- Para configurar o *Babel*, após a [[Instalando o Babel|instalação]], criamos um arquivo na raiz do nosso projeto com o nome: `babel.config.js`;
- Dentro desse arquivo, fazemos as seguintes configurações:
```js
const presets = ["@babel/preset-env"]

module.exports = { presets }
```
- Agora já temos o *Babel*, configurado;
- Para qualquer outra configuração, adicionamos nesse arquivo;
- Agora para podermos executar o *Babel*, usamos o comando:
```zsh
./node_modules/.bin/babel main.js --out-dir dist
```
- Desta maneira já conseguimos compilar o nosso código para uma versão mais antiga do javascript.