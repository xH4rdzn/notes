___
- Conseguimos usar o arquivo gerado pelo *Babel*, mas caso tenhamos que fazer alguma alteração no código, vamos precisar compilar novamente.
- Para poder deixar isso um pouco mais automático, vamos no arquivo `package.json`, e mudamos o `script`adicionando a flag `--watch`
```js
"scripts": {
	"build": "babel main.js --watch --out-dir ./dist"
}
```
- Desta maneira todas as alterações que fizermos irá refletir diretamente no código compilado.