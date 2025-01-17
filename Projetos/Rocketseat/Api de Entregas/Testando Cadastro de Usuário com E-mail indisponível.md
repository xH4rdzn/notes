___
- Agora vamos criar um teste para verificar se já tem um cadastro com um e-mail, para isso podemos adicionar o seguinte código logo após o primeiro [[Teste no Cadastro do Usuário|teste]];
```ts
it("should throw an error if user with same email already exists", async () => {
	const response = await request(app).post("/users").send({
		name: "Duplicate User",
		email: "testuser@example.com",
		password: "password123",
	})

	expect(reponse.status).toBe(400)
	expect(response.body.message).toBe("User with same email already exists")
})
```
- Desta maneira já conseguimos testar se ocorre um erro ao tentar cadastrar um usuário com um e-mail que já está cadastrado.
