___
- Agora vamos na pasta `controllers`, e vamos criar o arquivo `uploadsController.ts`e dentro dele vamos fazer o seguinte:
```ts
import { Request, Response } from 'express'

class UploadsController {
	async create(request: Request, response: Response) {
		return response.json({ message: "ok"})
	}
}

export { UploadsController }
```
- Agora na pasta `routes`, vamos criar o arquivo `uploadsRoutes.ts` e vamos fazer o seguinte:
```ts
import { Router } from 'express'
import { UploadsController } from '@/controllers/uploadsController'
import { verifyUserAuthorization } from "@/middlewares/verifyUserAuthorization"

const uploadsRoutes = Router()
const uploadsController = new UploadsController()


uploadsRoutes.use(verifyUserAuthorization(["employee"]))
uploadsRoutes.post("/", uploadsController.create)


export { uploadsRoutes }
```
- Agora vamos no arquivo `index.ts` que está dentro da pasta `routes` e adicionamos:
```ts
import { uploadsRoutes } from './uploadsRoutes'

routes.use("/uploads", uploadsRoutes)
```
- Agora voltamos ao arquivo `uploadsRoutes.ts`e adicionamos:
```ts
import { Router } from 'express'
import multer from 'multer'
import uploadsConfig from '@/configs/upload' 
import { UploadsController } from '@/controllers/uploadsController'
import { verifyUserAuthorization } from "@/middlewares/verifyUserAuthorization"


const uploadsRoutes = Router()
const uploadsController = new UploadsController()

const upload = multer(uploadConfig.MULTER)


uploadsRoutes.use(verifyUserAuthorization(["employee"]))
uploadsRoutes.post("/", upload.single("file") , uploadsController.create)


export { uploadsRoutes }
```
- Agora configuramos no `Insomnia`, para poder receber do campo `file`, ao enviarmos a requisição irá ser criado a pasta `tmp`que foi configurado anteriormente, juntamente com o arquivo que foi enviado.