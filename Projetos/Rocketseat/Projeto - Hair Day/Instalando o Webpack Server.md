___
- Vamos instalar o Webpack Server, usando o comando:
```zsh
npm i webpack-dev-server@4.15.1 --save-dev
```
- Agora voltamos ao arquivo `webpack.config.js`e continuamos suas configurações:
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
	devServer: {
		static: {
			directory: path.join(__dirname, "dist")
		},
		port: 3000,
		open: true,
		liveReload: true,
	}
}
```
- Agora voltamos ao arquivo `package.json`e adicionamos o seguinte `script`
```json
"dev": "webpack serve",
```