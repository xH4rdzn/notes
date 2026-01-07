___
- Os ***HTTP Status Codes***, são de importância semântica, e servem também para podermos  informar um erro, ou falta de algo.
- Os códigos mais utilizados são:
	- Informational responses -> 100 - 199
	- Successful responses -> 200 - 299
	- Redirection messages -> 300 - 399
	- Client Error responses -> 400 - 499
	- Server Error responses -> 500 - 599
- Para podermos mandar um ***HTTP Status Code***, fazemos como no exemplo abaixo:
```js
return res.writeHead(201).end()
```