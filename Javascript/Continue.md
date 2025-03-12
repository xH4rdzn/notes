___
- Encerra (pula) a execução das instruções na iteração atual e continua a execução do `loop` com a próxima iteração.
```js
let value = 0

for(i = 0; i < 10; i++) {
	if(value === 5){
		continue
	}
}
```