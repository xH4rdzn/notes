___
- Agora vamos incluir o CSS, no Webpack, para isso vamos instalar os plugins, usando o comando:
```zsh
npm i style-loader@3.3.3 css-loader@6.8.1 --save-dev
```
- Agora voltamos ao arquivo `webpack.config.js`e adicionamos as seguintes configurações:
```js
const path = require("path")
const HtmlWebpackPlugin = require("html-webpack-plugin")

module.exports = {
	target: "web",
	mode: "development",

	entry: path.resolve(__dirname, "src", "main.js"),
	output: {
		filename: "main.js",
		path: path.resolve(__dirname, "dist"),
	},
	devServer: {
		static: {
			directory: path.join(__dirname, "dist")
		},
		port: 3000,
		open: true,
		liveReload: true,
	},
	plugins: [new HtmlWebpackPlugin({
		template: path.resolve(__dirname, "index.html"),
		favicon: path.resolve("src", "assets", "scissors.svg"),
	})],
	module: {
		rules: [
			{
				test: /\.css$/,
				use: ["style-loader", "css-loader"],
			}
		]
	}
}
```
- Agora adicionamos o CSS no arquivo javascript da seguinte maneira:
```js
// Arquivo main.js da pasta src

"use strict"
import "./styles/global.css"
import "./styles/form.css"
import "./styles/schedule"
```
- Agora podemos ir no `index.html`e tirar a importação do CSS, pois o webpack vai ficar resposável por isso;
- Agora buildamos a nossa aplicação novamente com o comando:
```zsh
npm run build
```