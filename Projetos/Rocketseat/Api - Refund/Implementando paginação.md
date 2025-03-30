___
- Agora vamos implementar paginação na rota de listar as solicitações, para isso vamos continuar no método `index`
```ts
async index(request: Request, response: Response) {
	const querySchema = z.object({
		name: z.string().optional().default(""),
		page: z.coerce.number().optional().default(1),
		perPage: z.coerce.number().optional().default(10),
	})

	const { name, page, perPage } = querySchema.parse(request.query)

	const skip = (page - 1) * perPage

	

	const refunds = await prisma.refunds.findMany({
		skip,
		take: perPage,
		where: {
			user: {
				name: {
					contains: name.trim(),
				}
			}
		},
		orderBy: { createdAt: "desc"},
		include: { user: true },
	})


	// Obter o total de registros para calcular o número de páginas
	const totalRecords = await prisma.refunds.count({
		where: {
			user: {
				name: {
					contains: name.trim(),
				}
			}
		},
	})

	const totalPages = Math.ceil(totalRecords / perPage )
	

	return response.json({
		refunds,
		pagination: {
			page,
			perPage,
			totalRecords,
			totalPages: totalPages > 0 ? totalPages : 1,
		}
	})
}
```