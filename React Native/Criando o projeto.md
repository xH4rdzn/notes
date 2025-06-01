___
- Para criar um projeto *React Native*, precisamos navegar até a pasta onde queremos guardar os arquivos do nosso projeto, para isso usamos o comando abaixo:
```zsh
cd nomeDaPasta
```
- Ao chegarmos na pasta desejada podemos criar o nosso projeto, para isso usamos o comando:
```zsh
npx create-expo-app --template
```
- Agora escolhemos a opção ***Blank (Typescript)***;
- E depois damos um nome para esse projeto, e aguardamos ele criar e instalar as dependências.
- Agora navegamos até a pasta criada com o comando:
```zsh
cd nomeDaPasta
```
- E agora abrimos ela em nosso editor de código, no caso o **VSCode**, com o comando:
```zsh
code .
```

### Estruturas de pastas e arquivos
- Notamos que ao criar o nosso projeto, ele vai vir com algumas pastas e arquivos que são:
- `assets`-> É onde vamos ter as imagens que vão ser usadas em nossa aplicação.
- `node_modules`-> É a pasta onde ficam os arquivos dos módulos, essa pasta pode ser deletada, e não precisamos subir ela no *github*
- `.gitignore`-> arquivo onde colocamos as pastas ou arquivos que devem ser ignorados pelo ***git***;
- `package.json`e `package-lock.json`-> arquivo que salvam informações sobre as dependências do nosso projeto.
- `tsconfig.json`-> configurações do *typescript*
- `app.json`-> É onde temos informações sobre a aplicação.
- `index.ts`-> É o ponto de entrada da nossa aplicação.
- `App.tsx`-> É o componente que vai ser renderizado na tela.
