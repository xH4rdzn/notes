___
- Para compilar e executar o nosso código vamos utilizar a biblioteca `tsx`, podemos instalar ela com o comando:
```bash
npm i tsx -D
```
- Agora no nosso arquivo `package.json`, e vamos criar um script usando o `tsx`:
```json
"scripts": {
	"dev": "tsx watch src/server.ts"
}
```
- E agora podemos rodar o nosso servidor, usando o comando:
```bash
npm run dev
```

