___
- Dentro da pasta `configs`, vamos criar o arquivo `upload.ts`, para definirmos as configurações de upload;
- E também vamos instalar a dependência que irá realizar o upload, com o comando:
```zsh
npm i multer
```
- E também vamos instalar suas tipagens:
```zsh
npm i @types/multer -D
```
- Agora dentro do arquivo `upload.ts`, vamos fazer:
```ts
import multer from "multer"
import path from "node:path"
import crypto from "node:crypto"

const TMP_FOLDER = path.resolve(__dirname, "..", "..", "tmp")
const UPLOADS_FOLDER = path.resolve(TMP_FOLDER, "uploads")


const MAX_FILE_SIZE = 1024 * 1024 * 3

const ACCEPTED_IMAGE_TYPES = ["image/jpeg", "image/jpg", "image/png"]

const MULTER = {
	storage: multer.diskStorage({
		destination: TMP_FOLDER,
		filename(request, file, callback){
			const fileHash = crypto.randomBytes(10).toString("hex")
			const fileName = `${fileHash}-${file.originalname}`

			return callback(null, fileName)
		}
	})
}

export default {
	TMP_FOLDER,
	UPLOADS_FOLDER,
	MULTER,
	MAX_FILE_SIZE,
	ACCEPTED_IMAGE_TYPES,
}
```

