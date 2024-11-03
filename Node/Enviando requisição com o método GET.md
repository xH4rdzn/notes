___
- Para podermos fazer requisições do tipo `GET`, usamos métodos disponibilizados pelo `express`. Então para criar uma requisição do tipo `GET`, fazemos da seguinte maneira:
```ts
import express from "express"

const PORT = 3333

const app = express()

// Criando requisição do tipo GET
app.get("/", (request, response) => {
	response.send("Hello Express!")
})


app.listen(PORT, () => console.log(`Server is running on port ${PORT}`))

```
- Nota-se que como primeiro parâmetro do método `get`, passamos o `url`, e logo após passamos a função que será executada quando acessar essa rota.