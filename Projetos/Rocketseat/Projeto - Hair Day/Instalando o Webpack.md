___
- Vamos fazer a instalação do Webpack, com o comando:
```zsh
npm i webpack@5.89.0 webpack-cli@5.1.4 --save-dev
```
- Agora no arquivo `package.json`, vamos adicionar outro `script`
```json
"build" : "webpack"
```
- Agora dentro da pasta `src`, vamos criar um novo arquivo o `main.js`;
- Agora na raiz do nosso projeto, vamos criar o arquivo `webpack.config.js`, arquivo onde vamos definir as configurações do webpack
```js
const path = require("path")

module.exports = {
	target: "web",
	mode: "development",

	entry: path.resolve(__dirname, "src", "main.js"),
	output: {
		filename: "main.js",
		path: path.resolve(__dirname, "dist"),
	},
	
}
```