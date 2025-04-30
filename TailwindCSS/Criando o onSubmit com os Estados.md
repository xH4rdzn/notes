___
- Dentro da página de `SignIn`, vamos criar  a função que vai recuperar os dados do usuário.
- Para isso vamos ao arquivo `SignIn`, que está dentro da pasta `pages`e adicionamos:
```tsx
const [email, setEmail] = useState("")
const [password, setPassword] = useState("")
const [isLoading, setIsLoading] = useState(false)

function onSubmit(e: React.FormEvent) {
	e.preventDefault()
}
```
- Agora passamos a função para o `form`:
```tsx
<form onSubmit={onSubmit}>
	// Código
</form>
```
- Agora para o *input* passamos o `onChange`, da seguinte maneira:
```tsx
<Input onChange={(e) => setEmail(e.target.value)}
```
- Desta maneira conseguimos recuperar o que foi digitado pelo usuário;