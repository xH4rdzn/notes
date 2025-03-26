___
- Agora vamos capturar as informações do formulário e salvar na API;
- Dentro da pasta `src`, vamos criar a pasta `modules`;
- Dentro da pasta `modules`, vamos criar a pasta `form`;
- Dentro da pasta `form`, vamos criar o arquivo `submit.js` e dentro desse arquivo vamos fazer:
```js
const form = document.querySelector("form")
import dayjs from 'dayjs'
const selectedDate = document.getElementById("date")

// Data atual para formatar o input
const inputToday = dayjs(new Date()).format("YYYY-MM-DD")


// Carrega a Data atual
selectedDate.value = inputToday

// Define a data mínima como sendo a data atual
selectedDate.min = inputToday

form.onsubmit = (event) => {
	event.preventDefault()
}
```
- Agora importamos esse arquivo no arquivo `main.js`
```js
import "./modules/form/submit.js"
```