___
- Para carregar o favicon, adicionamos a seguinte configuração para o plugin do HTML;
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
	})]
}
```
- E agora só precisamos buildar novamente para poder carregar as novas configurações:
```zsh
npm run build
```
