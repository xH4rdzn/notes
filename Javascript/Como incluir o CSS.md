___
- Além de incluir o [[Como incluir o HTML|HTML]], conseguimos também incluir os arquivos CSS;
- No arquivo de configuração do Webpack, adicionamos as seguintes configurações:
```js
const path = require("path")
const HTMLWebpackPlugin = require("html-webpack-plugin")

module.exports = {
	entry: path.resolve(__dirname, "src", "js", "index.js"),
	output: {
		filename: "main.js",
		path: path.resolve(__dirname, "dist")
	},
	mode: "development",
	plugins: [new HTMLWebpackPlugin()],
	module: {
		rules: [{
			test: /\.css$/i,
			use: ["sytle-loader", "css-loader"],
			exclude: "/node_modules"
		}]
	}
}
```
- E agora instalamos esse plugins com o comando:
```zsh
npm install style-loader css-loader --save-dev
```
- Agora ao executarmos o comando de build ele irá compreender os arquivos `.css`, e assim irá aplicar nossas estilizações
- Precisamos importar o `css`, diretamente no javascript
```js
import "../css/styles.css"
```

