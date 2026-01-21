___
- Quando usamos *microframeworks* ou até mesmo *frameworks*, passamos os ***Route Params***, com a simbologia de `:`, mas no node puro não temos isso.
- Para isso, vamos fazer o seguinte:
- Na pasta `src`, vamos criar a pasta `utils` e dentro dela vamos criar o arquivo `build-route-path.js`.
```js
export function buildRoutePath(path) {
	const routeParametersRegex = /:([a-zA-Z]+)/g
}
```