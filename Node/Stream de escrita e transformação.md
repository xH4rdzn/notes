___
- Para criar streams de escrita, precisamos fazer a importação do `Writable`e ela necessáriamente possui o método `_write()` que recebe 3 parâmetros o *chunk, encoding, callback*:
```js
import { Writable } from 'node:stream'

class MultiplyByTenStream extends Writable {
	_write(chunk, encoding, callback) {
		console.log(Number(chunk.toString()) * 10)
		callback()
	}
}
```
- A função de callback é chamada toda vez que é terminado as escrita dos dados daquela stream.

- Para criar uma stream, que transformar os dados, precisamos fazer a importação do `Transform`.
- Essa stream, serve para poder transformar dados em outros dados. Normalmente essas streams ficam no intermédio entre as streams de leitura e escrita.
```js
import { Transform } from 'node:stream'

class InverseNumberStream extends Transform {
	_transform(chunk, encoding, callback) {
		const transformed = Number(chunk.toString()) * -1
		
		callback(null, Buffer.from(String(transformed)))
	}
}
```
- O primeiro parâmetro do `callback`de `Transform`é o erro, caso de erro, precisamos mandar ele como primeiro parâmetro.
- O segundo parâmetro é o dado transformado.