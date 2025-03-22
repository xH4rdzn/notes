___
- *Shallow Copy* (cópia superficial): não pega os itens aninhados.
```js
const htmlCourse = {
	course: "HTML",
	students: [{name: "Igor", email: "igor@email.com"}]
}

const jsCourse = {
	...htmlCourse,
	course: "Javascript",
}

console.log(htmlCourse, jsCourse)

// Agora se adicionarmos um novo estudante em jsCourse, ele também vai adicionar em htmlCourse

jsCourse.students.push({name: "Lucas", email: "lucas@email.com"})
```
- Como `students`é uma propriedade *aninhada*, então ele não faz uma cópia, ele só faz uma referência.
- Para resolver esse problema fazemos uma **Deep Copy**, como demostrado no exemplo abaixo:
```js
const htmlCourse = {
	course: "HTML",
	students: [{name: "Igor", email: "igor@email.com"}]
}

const jsCourse = {
	...htmlCourse,
	course: "Javascript",
	students: [...htmlCourse.students]
}
```
- Como mostrado no exemplo acima, agora podemos adicionar apenas estudantes, de maneira separada, o `jsCourse`não altera a propriedade `students`que está em `htmlCourse`;
- Ainda existe outra maneira de fazer uma cópia mais profunda de uma propriedade aninhada:
```js
const htmlCourse = {
	course: "HTML",
	students: [{name: "Igor", email: "igor@email.com"}]
}

const jsCourse = {
	...htmlCourse,
	course: "Javascript"
}

jsCourse.students = [
	...htmlCourse.students,
	{name: "Lucas", email: "lucas@email.com"}
] 
```
- Usamos o *Deep Copy*, quando temos objetos mais complexos, que podem ter outros *objetos* ou *arrays* em seu conteúdo;