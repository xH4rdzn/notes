___
- No nosso método `index`, vamos continuar:
```ts
async index(request: Request, response: Response) {
	const querySchema = z.object({
		name: z.string().optional().default(""),
	})

	const { name } = querySchema.parse(request.query)
	
	const refunds = await prisma.refunds.findMany({
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

	

	return response.json(refunds)
}
```