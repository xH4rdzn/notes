___
- Para levar os assets para a nossa pasta `dist`, vamos usar um plugin, que vamos instalar usando o comando:
```zsh
npm i copy-webpack-plugin@11.0.0 --save-dev
```
- Agora voltamos ao arquivo de configuração do webpack e fazemos o seguinte:
```js
const path = require("path")
const HtmlWebpackPlugin = require("html-webpack-plugin")
const CopyWebpackPlugin = require("copy-webpack-plugin")

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
	plugins: [
		new HtmlWebpackPlugin({
			template: path.resolve(__dirname, "index.html"),
			favicon: path.resolve("src", "assets", "scissors.svg"),
	}),
		new CopyWebpackPlugin({
			patterns: [
				{
					from: path.resolve(__dirname, "src", "assets"),
					to: path.resolve(__dirname, "dist", "src", "assets")
				}
			]
		}),
	
	],
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