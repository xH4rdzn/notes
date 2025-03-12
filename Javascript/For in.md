___
- Executa iterações a partir de um objeto e percorre as *propriedades*.
```js
let person = {
	name: "Igor",
	surname: "Coelho",
	email: "igor@email.com",
}

for (let property in person){
	console.log(person[property])
}
```
- Podemos usar esse loop para *arrays*
```js
let students = ["Igor", "Rodrigo", "Amanda"]

for (let index in students) {
	console.log(students[index])
}
```
