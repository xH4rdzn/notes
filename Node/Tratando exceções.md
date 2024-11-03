___
- Para poder tratar as exceções, vamos no arquivo `server.ts`, e depois de todo o código, menos o método `listen`, vamos fazer o seguinte:
```ts
app.use((error, request: Request, response: Response, next) => {
	response.status(500).json({message: error.message})
})
```
- Agora quando ocorrer uma exceção ele vai devolver uma reposta mais amigável e não irá parar a nossa aplicação.