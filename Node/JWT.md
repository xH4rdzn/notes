___
- `JWT` -> JSON Web Token
- Um padrão de mercado que define um token no formato `JSON` para troca de informações de forma segura e compacta;
- Um `Token JWT`, se divide em 3 partes que são:
	- `HEADER`
	- `PAYLOAD`
	- `VERIFY SIGNATURE`
- No `Header`, definimos o algoritmo e o tipo do Token;
- No `Payload`, definimos o conteúdo do Token;
- O `Verify Signature`, serve para garantir a integridade do Token;

#### Onde usar JWT
- Vamos, por exemplo, em um cenário de autorização. Depois que o usuário estiver conectado, é possível observar cada requisição e verificar se inclui o `JWT` e verificando se o usuário tem autorização para acessar os recursos da API.

- Podemos testar o `JWT` no site: [jwt.io](https://jwt.io/)
