___
- Anteriormente criamos o `schema`, agora vamos utilizar
```tsx
const  schema = yup.object({
	name: yup.string().required("Nome é obrigatório"),
	date: yup.string().required("Data é obrigatória"),
	subject: yup.string().required("Selecione um assunto"),
	description: yup.string().required("Descrição é obrigatória").min(10, "A descrição precisa ter pelo menos 10 dígitos")
})
```