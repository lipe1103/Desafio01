# Dicionário para armazenar os contatos
agenda = {}

# Função para exibir o menu
def mostrar_menu():
    print("\nEscolha uma opção:")
    print("1. Adicionar contato")
    print("2. Visualizar contatos")
    print("3. Editar contato")
    print("4. Marcar/Desmarcar contato como favorito")
    print("5. Ver lista de favoritos")
    print("6. Apagar contato")
    print("0. Sair")

# Função para adicionar um contato
def adicionar_contato():
    nome = input("Nome: ")
    telefone = input("Telefone: ")
    email = input("Email: ")
    favorito = input("Favorito? (s/n): ").lower() == 's'

    # Adiciona o contato no dicionário
    agenda[nome] = {
        "telefone": telefone,
        "email": email,
        "favorito": favorito
    }
    print(f"Contato {nome} adicionado com sucesso!")

# Função para exibir os contatos
def visualizar_contatos():
    if not agenda:
        print("Nenhum contato cadastrado.")
    else:
        for nome, dados in agenda.items():
            favorito = "Sim" if dados["favorito"] else "Não"
            print(f"\nNome: {nome}")
            print(f"Telefone: {dados['telefone']}")
            print(f"Email: {dados['email']}")
            print(f"Favorito: {favorito}")

# Função para editar um contato
def editar_contato():
    nome = input("Digite o nome do contato que deseja editar: ")
    if nome in agenda:
        telefone = input("Novo telefone: ")
        email = input("Novo email: ")
        agenda[nome]["telefone"] = telefone
        agenda[nome]["email"] = email
        print(f"Contato {nome} atualizado com sucesso!")
    else:
        print(f"Contato {nome} não encontrado.")

# Função para marcar/desmarcar um contato como favorito
def marcar_favorito():
    nome = input("Digite o nome do contato: ")
    if nome in agenda:
        agenda[nome]["favorito"] = not agenda[nome]["favorito"]
        status = "favorito" if agenda[nome]["favorito"] else "não favorito"
        print(f"Contato {nome} agora é {status}.")
    else:
        print(f"Contato {nome} não encontrado.")

# Função para exibir contatos favoritos
def ver_favoritos():
    favoritos = {nome: dados for nome, dados in agenda.items() if dados["favorito"]}
    if favoritos:
        print("\nContatos favoritos:")
        for nome, dados in favoritos.items():
            print(f"\nNome: {nome}")
            print(f"Telefone: {dados['telefone']}")
            print(f"Email: {dados['email']}")
    else:
        print("Nenhum contato marcado como favorito.")

# Função para apagar um contato
def apagar_contato():
    nome = input("Digite o nome do contato que deseja apagar: ")
    if nome in agenda:
        del agenda[nome]
        print(f"Contato {nome} removido com sucesso!")
    else:
        print(f"Contato {nome} não encontrado.")

# Função principal
def executar():
    while True:
        mostrar_menu()
        escolha = input("Escolha uma opção: ")

        if escolha == "1":
            adicionar_contato()
        elif escolha == "2":
            visualizar_contatos()
        elif escolha == "3":
            editar_contato()
        elif escolha == "4":
            marcar_favorito()
        elif escolha == "5":
            ver_favoritos()
        elif escolha == "6":
            apagar_contato()
        elif escolha == "0":
            print("Saindo da agenda...")
            break
        else:
            print("Opção inválida! Tente novamente.")

# Executa o programa
executar()
