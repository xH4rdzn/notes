___
- Para poder configurar o webpack, no `script`que criamos [[Instalando e executando o Webpack|anteriormente]], alteramos ele para:
```json
"scripts": {
	"build": "Webpack"
}
```
- Agora na raiz do nosso projeto criamos o arquivo `webpack.config.js`, e dentro dele fazemos as seguintes configurações:
```js
const path = require("path")

module.exports = {
	entry: path.resolve(__dirname, "src", "js", "index.js"),
	output: {
		filename: "main.js",
		path: path.resolve(__dirname, "dist")
	},
	mode: "development"
}
```