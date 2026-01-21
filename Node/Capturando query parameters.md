____
- Para podermos capturar os *query params*, precisamos modificar a nossa ***RegEx***
```js
export function buildRoutePath(path) {
	const routeParametersRegex = /:([a-zA-z])/g
	
	const pathWithParams = path.replaceAll(routeParametersRegex, '([a-z0-9\-_]+)')
	
	const pathRegex = new RegExp(`^${pathWithParams}(?<query>\\?(.*))?$`)
	
	return pathRegex
}
```
- Agora dentro da pasta `utils`, vamos criar outra função, que vamos chamar ela de `extract-query-params.js`
```js
export function extractQueryParams(query) {
	return query.substr(1).split('&').reduce((queryParams, param) => {
		const [key, value] = param.split('=')
		
		queryParams[key] = value
		
		return queryParams	
	}, {})
}
```
- Agora em nosso servidor, vamos fazer uma alteração para poder recuperar tanto os *query params* como os *route params*.
```js
if(route) {
	const routeParams = req.url.match(route.path)

	const { query, ...params} = routeParams.groups
	
	req.params = params
	req.query = query ? extractQueryParams(query) : {}

	return route.handler(req,res)
}
```