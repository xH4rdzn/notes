___
- Para criar *aliases* de importação vamos no arquivo `tsconfig.json`e procuramos a opção *baseUrl* e *paths* e configuramos elas como no exemplo abaixo:
```json
"baseUrl": "./",
"paths": {
	"@/*": ["./src/*"],
}
```