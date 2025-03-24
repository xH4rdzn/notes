___
- Nas configurações do Webpack, já incluimos [[Como incluir o HTML|HTML]] e [[Como incluir o CSS|CSS]], agora vamos incluir o *Babel*;
- Primeiros instalamos o *Babel*, com o comando:
```zsh
npm install @babel/core @babel/preset-env babel-loader --save-dev
```
- Após a instalação, no arquivo de configurações do Webpack, logo após a configuração para incluir o css adicionamos:
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
		},
		{
			text: /\.js$/i,
			exclude: "/node_modukes",
			use: {
				loader: "babel-loader",
				options: {
					presets: [["@babel/preset-env", {targets: "defaults"}]],
				},
			}
		}
		]
	}
}
```