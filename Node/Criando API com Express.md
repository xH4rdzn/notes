___
- Agora para criar o nosso servidor com o `express`, precisamos instanciar o `express`, e fazemos da seguinte maneira:
```ts
import express from "express"

const app = express()
```
- Após isso a partir da variável `app`, podemos usar vários métodos que são disponibilizados pelo `express`.
- Um deles é o método `listen`, que indica em qual porta o nosso servidor vai receber as requisições.
```ts
import express from "express"

const app = express()

app.listen(3333)
```
- O método `listen`, recebe a porta do nosso servidor como parâmetro, então fazemos da seguinte maneira:
```ts
import express from "express"

const PORT = 3333

const app = express()

app.listen(PORT, () => console.log(`Server is running on port ${PORT}`))
```