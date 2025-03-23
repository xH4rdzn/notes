___
- Para instalar o `Webpack`, usamos o comando:
```zsh
npm install webpack webpack-cli --save-dev
```
- Após a instalação no arquivo `package.json`, podemos criar um `script`, para automatizar o processo:
```json
"scripts": {
	"build": "webpack ./src/js/index.js"
}
```
- E agora usamos o comando para executar o webpack:
```zsh
npm run build
```
- Desta maneira ele irá gerar apenas um arquivo javascript;