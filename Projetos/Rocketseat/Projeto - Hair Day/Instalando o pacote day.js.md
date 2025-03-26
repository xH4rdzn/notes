___
- Agora vamos instalar o `day.js`, para poder manipular datas;
- Vamos instalar com o comando:
```zsh
npm i dayjs@1.11.10
```
- Agora dentro da pasta `src`, vamos criar o arquivo `dayjs.js`, para colocarmos as configurações do `DayJs`
```js
import dayjs from 'dayjs'
import "dayjs/locale/pt-br"

dayjs.locale("pt-br")
```
- Agora vamos no arquivo `main.js`, e vamos fazer a importação:
```js
"use strict"

import "./libs/dayjs.js"

// CSS
// Importações do CSS
```