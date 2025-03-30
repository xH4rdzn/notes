___
- Agora que a nossa API já esta fazendo upload de arquivos, vamos fazer uma rota, para visualizar esses arquivos;
- Para isso vamos no arquivo `app.ts`e vamos adicionar o seguinte trecho:
```ts
import uploaadConfig from './configs/upload'

app.use("uploads", express.static(uploadConfig.UPLOADS_FOLDER))
```
- Agora para acessar esses arquivos, podemos fazer o acesso seguindo o exemplo de link abaixo:
```link
http://localhost:3333/uploads/nomeDaImagem.jgp
```
