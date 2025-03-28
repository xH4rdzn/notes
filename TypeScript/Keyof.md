___
- O `keyof`, é usado para extrair as chaves de um objeto e usar como tipagem
```ts
const icons = {
	"home": "./path/home.svg",
	"add": "./path/add.svg",
	"remove": "./path.remove.svg"
}

type Icon = typeof icons

// usando o keyof
const icon: keyof Icon = "add"
```
- Desta maneira conseguimos selecionar apenas as chaves de uma tipagem;