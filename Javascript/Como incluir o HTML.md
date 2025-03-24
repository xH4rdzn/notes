___
- Como usamos o [[Configurando o Webpack|Webpack]], para empacotar o código Javascript, podemos usar ele para poder empacotar o `HTML`, para isso precisamos instalar o plugin que faz isso, com o comando:
```zsh
npm install --save-dev html-webpack-plugin
```
- Agora no arquivo de configurações do Webpack e o adicionamos da seguinte maneira:
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
}
```
- Agora ao executarmos o `script`que criamos para rodar o Webpack, ele vai levar o arquivo HTML para a pasta na qual configuramos;