___
- Para fazer um [Inner Join|SELECT com JOIN](../Banco%20De%20dados/Inner%20Join.md), fazemos da seguinte maneira:
```ts
app.get("/courses/:id/modules", async (request: Request, response: Response) => {
	const courses = await knex("courses")
		.select("course_modules.id", "course_modules.name AS module", "courses.name AS course" )
		.join("course_modules", "courses.id", "course_modules.course_id")
	

	return response.json(courses)
})
```