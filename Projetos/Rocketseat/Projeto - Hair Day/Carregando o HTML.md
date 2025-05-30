___
- Para incluir o HTML, precisamos fazer a instalação de um plugin do Webpack, para isso vamos usar o comando:
```zsh
npm i html-webpack-plugin@5.6.0 --save-dev
```
- E agora no arquivo `webpack.config.js`, vamos adicionar a seguinte linha:
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
	})]
}
```
- Agora executamos o comando de `build`, para poder empacotar o Html;
```zsh
npm run build
```