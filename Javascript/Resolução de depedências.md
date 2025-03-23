___
### Versionamento semântico
- Padrão de atualizações de versões que oferece um modelo fácil de entender o que mudou em uma versão.
- Representados na ordem:
	- 9.1.3
	- Major -> primeiro número
	- Minor -> segundo número
	- Patch -> terceiro número
- Onde:
	- *Major (Versão Principal)* -> Aumenta quando são feitas alterações incompatíveis. Isso significa que, se você atualizar para uma nova versão principal, pode haver alterações que quebrarão a compatibilidade com versões anteriores.
	- *Minor (Versão Menor)* -> Aumenta quando são adicionadas novas funcionalidades de maneira compatível com versões anteriores. As atualizações de ver~soa menor não devem introduzir alterações que quebram a compatibilidade com o código existente.
	- *Patch (Versão de Correção)* -> Aumenta quando são feitas correções de bugs compatíveis com versões anteriores. Isso significa que essas correções não devem introduzir novas funcionalidades ou quebrar a compatibilidade.

### Convenções
- O npm utiliza convenções para gerenciar a resolução de dependências e garantir que as instalações subsequentes mantenham a compatibilidade com versões utilizadas na aplicação.

### ~
- O til(~) permite atualizações automáticas para versões compatíveis. Isso permite receber patches e correções de bugs
```json
{
	"dependecies": {
		"package-name": "~4.17.20"
	}
}
```

### ^
- O acento circunflexo (^) indica que o npm pode instalar automaticamente a versão mais recente compatível, mas não a próxima versão incompatível 
- Isso permite receber patches, correções de bugs e pequenas alterações de versão, mas não grandes alterações de versão.
```json
{
	"dependecies": {
		"package-name": "^4.17.20"
	}
}
```

### @
- Quando você usa @ antes da versão, indica uma versão exata. O npm instalará exatamente a versão especificada.
```zsh
npm install dayjs@1.11.10
```
