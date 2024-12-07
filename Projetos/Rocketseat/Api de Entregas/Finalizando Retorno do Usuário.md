___
- Como criamos o [[Recuperando o Usuário|controller de autorização]], agora precisamos devolver os dados do usuário, porém sem a senha, para isso podemos usar a estrategia:
```ts
const { password: hashedPassword , ...userWithoutPassoword } = user
```
- Agora podemos devolver tanto o `token`, como o usuário sem a senha:
```Ts
return response.json({ token, user: userWithoutPassword})
```