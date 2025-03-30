___
- Agora vamos manipular esse arquivo, caso ele não passe em nossas validações, vamos apagar esse arquivo, para isso dentro da pasta `src`, vamos criar a pasta `providers` e dentro dessa pasta vamos criar o arquivo `diskStorage.ts`
```ts
import fs from 'node:fs'
import path from 'node:path'


import uploadConfig from '@/configs/upload'

export class DiskStorage {
	async saveFile(file: string) {
		const tmpPath = path.resolve(uploadConfig.TMP_FOLDER, file)
		const destPath = path.resolve(uploadConfig.UPLOADS_FOLDER, file)

		try {
			await fs.promises.access(tmpPath)
		} catch(error){
			console.log(error)
			throw new Error(`Arquivo não encontrado: ${tmpPath}`)
		}

		await fs.promises.mkdir(uploadConfig.UPLOADS_FOLDER, { recursive: true})
		await fs.promises.rename(tmpPath, destPath)


		return file
	}
	async deleteFile(file: string, type: "tmp" | "upload") {
		const pathFile = type === 'tmp' ? uploadConfig.TMP_FOLDER : uploadConfig.UPLOADS_FOLDER

		const filePath = path.resolve(pathFile, file)


		try {
			await fs.promises.stat(filePath)
		} catch {
			return 
		}

		await fs.promises.unlink(filePath)
		
	}
}
```
- Agora voltamos ao nosso controller de uploads e fazemos o seguinte:
```ts
import { Request, Response } from 'express'
import { z } from 'zod'
import uploadConfig from '@/configs/upload'
import { DiskStorage } from '@/providers/diskStorage'

class UploadsController {
	async create(request: Request, response: Response) {
		const diskStorage = new DiskStorage()
		try {
			const fileSchema = z.object({
				filename: z.string().min(1, 'Arquivo é obrigatório'),
				mimetype: z.string().refine((type) => uploadConfig.ACCEPTED_IMAGE_TYPES.includes(type), `Formato de arquivo inválido. Formatos permitidos:  ${uploadConfig.ACCEPTED_IMAGE_TYPES}`),
				size: z.number().positive().refine((size) => size <= uploadConfig.MAX_FILE_SIZE, `Arquivo excede o tamanho máximo de ${uploadConfigs.MAX_SIZE}`),
			}).passthrough()

			const  file  = fileSchema.parse(request.file)

			const filename = await diskStorage.saveFile(file.filename)

			response.json({ filename })
		} catch(error) {

			if(error instanceof ZodError) {
				if(request.file) {
					await diskStorage.deleteFile(request.file.filename, "tmp")
				}


				throw new AppError(error.issues[0].message)

			}

			throw error
		}
		
	}
}

export { UploadsController }
```