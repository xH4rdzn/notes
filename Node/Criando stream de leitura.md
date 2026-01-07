___
- No *Node*, toda porta de entrada e saída é automaticamente uma stream.
- Para criar uma stream de leitura, vamos fazer os passos abaixo:
```js
import { Readable } from 'node:stream'

class OneToHundredStream extends Readable {
	index = 1
	
	_read() {
		const i = this.index++
		
		if (i > 100) {
			this.push(null)
		} else {
			const buf = Buffer.from(String(i))
			
			this.push(buf)
		}
	}
}
```
- Streams não recebem dados de tipos primitivos, apenas *Strings*;