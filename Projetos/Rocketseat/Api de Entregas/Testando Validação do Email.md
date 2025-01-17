___
- Agora vamos criar um teste para validar um email para isso fazemos da seguinte maneira:
```ts
it("should throw a validation error if email is invalid", async () => {
	const response = await request(app).post("/users").send({
		name: "Test User",
		email: "invalid-email",
		password: "password123",
	})

	expect(response.status).toBe(400)
	expect(response.body.message).toBe("validation error")
})
```