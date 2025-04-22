___
- Para recuperar os erros, de dentro do próprio `useForm`, desestruturamos o `formState`e dentro dele pegamos os `errors`:
```tsx
const { control, handleSubmit, formState: {errors}} = useForm<FormDate>({
	resolver: yupResolver(schema)
})
```
- Agora para exibir os erros de validação, fazemos da seguinte maneira:
```tsx
{errors.name?.message && <span>{errors.name.message}</span>}
```
- E podemos fazer isso para todos os `inputs`do nosso formulário;