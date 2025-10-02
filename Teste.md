___
```python
# ---------------------------------------------------------
# Sistema de Gerenciamento de Contatos Comerciais
# Desenvolvido para atender às exigências do enunciado
# Autor: Igor Rodrigues
# ---------------------------------------------------------

# Mensagem de boas-vindas (Exigência A)
print("Bem-vindo ao Sistema de Gerenciamento de Contatos Comerciais - Desenvolvido por Igor Rodrigues")

# Lista para armazenar os contatos (Exigência B e G)
lista_contatos = []

# Variável id_global (substituir pelo seu RU real, exemplo: 1234567)
id_global = 1234567

# ---------------------------------------------------------
# Função para cadastrar contato (Exigência C)
def cadastrar_contato(id):
    # Solicita os dados do contato
    nome = input("Informe o nome do contato: ")
    atividade = input("Informe a atividade do contato: ")
    telefone = input("Informe o telefone do contato: ")

    # Cria o dicionário com os dados
    contato = {
        "id": id,
        "nome": nome,
        "atividade": atividade,
        "telefone": telefone
    }

    # Copia para a lista de contatos
    lista_contatos.append(contato.copy())
    print("Contato cadastrado com sucesso!\n")

# ---------------------------------------------------------
# Função para consultar contatos (Exigência D)
def consultar_contatos():
    while True:
        print("\n--- MENU CONSULTAR ---")
        print("1. Consultar Todos")
        print("2. Consultar por Id")
        print("3. Consultar por Atividade")
        print("4. Retornar ao menu")
        
        opcao = input("Escolha uma opção: ")

        if opcao == "1":
            print("\n--- LISTA DE CONTATOS ---")
            for contato in lista_contatos:
                print(contato)

        elif opcao == "2":
            id_busca = input("Informe o id do contato: ")
            encontrado = False
            for contato in lista_contatos:
                if str(contato["id"]) == id_busca:
                    print(contato)
                    encontrado = True
            if not encontrado:
                print("Id não encontrado.")

        elif opcao == "3":
            atividade_busca = input("Informe a atividade: ")
            encontrados = [c for c in lista_contatos if c["atividade"].lower() == atividade_busca.lower()]
            if encontrados:
                for contato in encontrados:
                    print(contato)
            else:
                print("Nenhum contato encontrado com essa atividade.")

        elif opcao == "4":
            return  # Retorna ao menu principal

        else:
            print("Opção inválida. Tente novamente.")

# ---------------------------------------------------------
# Função para remover contato (Exigência E)
def remover_contato():
    while True:
        id_remover = input("Informe o id do contato a remover: ")
        encontrado = False
        for contato in lista_contatos:
            if str(contato["id"]) == id_remover:
                lista_contatos.remove(contato)
                print("Contato removido com sucesso!")
                encontrado = True
                return
        if not encontrado:
            print("Id inválido. Tente novamente.")

# ---------------------------------------------------------
# Estrutura de menu principal (Exigência F)
while True:
    print("\n--- MENU PRINCIPAL ---")
    print("1. Cadastrar Contato")
    print("2. Consultar Contato")
    print("3. Remover Contato")
    print("4. Encerrar Programa")

    escolha = input("Escolha uma opção: ")

    if escolha == "1":
        cadastrar_contato(id_global)
        id_global += 1  # incrementa o id_global
    elif escolha == "2":
        consultar_contatos()
    elif escolha == "3":
        remover_contato()
    elif escolha == "4":
        print("Programa encerrado. Até logo!")
        break
    else:
        print("Opção inválida. Tente novamente.")
```
```