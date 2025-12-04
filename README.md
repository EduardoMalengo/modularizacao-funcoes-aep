# modularizacao-funcoes-aep
Repositório técnico focado na construção de módulos funcionais, testes unitários simples e validação de entrada/saída em ambiente controlado.

Perfeito, Eduardo — agora vou **refinar para o padrão acadêmico**, com tom formal, objetivo, técnico **e sem perder clareza**.
Isso aqui passa tranquilo em qualquer avaliação.

Segue o **README acadêmico** pronto para colar no GitHub **ou colocar no PDF da entrega**:

---

# 🏥 **Sistema de Cadastro e Estatísticas de Pacientes**

### *README — Versão Acadêmica*

## 📘 **1. Introdução**

Este projeto foi desenvolvido como requisito da disciplina de Algoritmos e Programação, com foco na aplicação prática dos conceitos de estruturas de dados básicas, modularização, lógica condicional, repetição e manipulação de coleções. O objetivo central é implementar um sistema simples e funcional para cadastro e análise estatística de pacientes.

---

## 🎯 **2. Objetivos do Sistema**

* Implementar um sistema de cadastro utilizando **listas e dicionários**.
* Exibir estatísticas essenciais com base nos dados inseridos.
* Aplicar validação de entradas e tratamento de erros.
* Consolidar boas práticas de programação estruturada.
* Oferecer interface textual simples e intuitiva.

---

## ⚙️ **3. Funcionalidades Desenvolvidas**

O sistema contempla os seguintes módulos:

### **Cadastro de Pacientes**

* Nome
* Idade
* Telefone
* Validações básicas (idade numérica, campos obrigatórios)

### **Listagem Completa**

* Exibição de todos os pacientes cadastrados
* Formatação limpa para fácil leitura

### **Busca pelo Nome**

* Busca parcial ou completa
* Resultado em tempo real
* Insensível a maiúsculas/minúsculas

### **Estatísticas Automáticas**

* Quantidade total de pacientes
* Média de idade
* Idade mínima
* Idade máxima

### **Menu Interativo**

* Loop contínuo até o usuário escolher sair
* Tratamento de erros para opções inválidas

---

## 🛠️ **4. Tecnologias e Conceitos Utilizados**

* **Python 3**
* Listas
* Dicionários
* Estruturas condicionais (`if/else`)
* Estruturas de repetição (`while`)
* Tratamento de exceções (`try/except`)
* Funções (na versão modularizada)

---

## 📁 **5. Estrutura do Repositório**

```
/src
   v1_sem_funcoes/
      main.py
   v2_modularizado/
      main.py
/docs
   relatorio.pdf
   evidencias/
/README.md
```

---

## ▶️ **6. Como Executar o Programa**

1. Instale Python 3 (ou utilize Replit).
2. Abra o terminal dentro da pasta referente à versão desejada.
3. Execute o comando:

```bash
python main.py
```

---

## 🧪 **7. Exemplos de Uso**

### **Menu Principal**

```
1 - Cadastrar paciente
2 - Listar pacientes
3 - Buscar paciente pelo nome
4 - Estatísticas
0 - Sair
```

### **Exemplo de Saída de Estatísticas**

```
Total de pacientes: 3
Média de idade: 42.6 anos
Paciente mais novo: Ana (18 anos)
Paciente mais velho: Ricardo (70 anos)
```

---

## 🔍 **8. Considerações Finais**

O projeto atende integralmente aos requisitos da disciplina, demonstra domínio das estruturas fundamentais da linguagem e apresenta um sistema funcional, organizado e escalável para futuras melhorias (validações avançadas, persistência em arquivo, interface gráfica, etc.).

---

## 🧑‍💻 **9. Autor**

**Eduardo**
Curso: Analise e Desenvolvimento de Sistemas - (ADS)
Disciplina: Algoritmos e Programação
Instituição: Universidade institucional Anhanguera 



/src
   /v1_sem_funcoes
       main.c
   /v2_modularizado
       main.c
       funcoes.c
       funcoes.h
/docs
   relatorio.pdf
   evidencias/
README.md


# === SISTEMA CLÍNICA VIDA+ ===
# Desenvolvido para o Projeto Integrado

pacientes = []

def cadastrar_paciente():
    print("\n--- CADASTRAR PACIENTE ---")
    nome = input("Nome do paciente: ").strip()

    # valida idade
    while True:
        try:
            idade = int(input("Idade: "))
            if idade <= 0:
                print("Idade inválida. Digite novamente.")
                continue
            break
        except:
            print("Digite um número válido.")

    telefone = input("Telefone: ").strip()

    paciente = {
        "nome": nome,
        "idade": idade,
        "telefone": telefone
    }

    pacientes.append(paciente)
    print("Paciente cadastrado com sucesso!\n")


def estatisticas():
    print("\n--- ESTATÍSTICAS DA CLÍNICA ---")

    if len(pacientes) == 0:
        print("Nenhum paciente cadastrado.\n")
        return

    total = len(pacientes)
    media_idade = sum(p["idade"] for p in pacientes) / total
    mais_novo = min(pacientes, key=lambda p: p["idade"])
    mais_velho = max(pacientes, key=lambda p: p["idade"])

    print(f"Total de pacientes: {total}")
    print(f"Idade média: {media_idade:.1f}")
    print(f"Paciente mais novo: {mais_novo['nome']} ({mais_novo['idade']} anos)")
    print(f"Paciente mais velho: {mais_velho['nome']} ({mais_velho['idade']} anos)\n")


def buscar_paciente():
    print("\n--- BUSCAR PACIENTE ---")
    nome_busca = input("Digite o nome para buscar: ").strip().lower()

    encontrados = [p for p in pacientes if nome_busca in p["nome"].lower()]

    if encontrados:
        print("\nPacientes encontrados:")
        for p in encontrados:
            print(f"- {p['nome']} | {p['idade']} anos | {p['telefone']}")
    else:
        print("Nenhum paciente encontrado.")
    print()


def listar_pacientes():
    print("\n--- LISTA DE PACIENTES ---")

    if len(pacientes) == 0:
        print("Nenhum paciente cadastrado.\n")
        return

    for i, p in enumerate(pacientes, start=1):
        print(f"{i}. {p['nome']} | {p['idade']} anos | {p['telefone']}")
    print()


def menu():
    while True:
        print("=== SISTEMA CLÍNICA VIDA+ ===")
        print("1. Cadastrar paciente")
        print("2. Ver estatísticas")
        print("3. Buscar paciente")
        print("4. Listar todos os pacientes")
        print("5. Sair")

        opcao = input("Escolha uma opção: ")

        if opcao == "1":
            cadastrar_paciente()
        elif opcao == "2":
            estatisticas()
        elif opcao == "3":
            buscar_paciente()
        elif opcao == "4":
            listar_pacientes()
        elif opcao == "5":
            print("Encerrando sistema. Até mais!")
            break
        else:
            print("Opção inválida, tente novamente.\n")


menu()

# === SISTEMA CLÍNICA VIDA+ ===

pacientes = []

def cadastrar_paciente():
    print("\n--- Cadastro de Paciente ---")
    nome = input("Nome do paciente: ").strip()
    
    # valida idade
    while True:
        try:
            idade = int(input("Idade: "))
            if idade <= 0:
                print("Idade inválida. Digite um número positivo.")
                continue
            break
        except ValueError:
            print("Digite apenas números.")

    telefone = input("Telefone: ").strip()

    paciente = {
        "nome": nome,
        "idade": idade,
        "telefone": telefone
    }
    pacientes.append(paciente)
    print("Paciente cadastrado com sucesso!\n")


def ver_estatisticas():
    if not pacientes:
        print("\nNenhum paciente cadastrado.\n")
        return

    total = len(pacientes)
    idades = [p["idade"] for p in pacientes]
    media = sum(idades) / total

    mais_novo = min(pacientes, key=lambda p: p["idade"])
    mais_velho = max(pacientes, key=lambda p: p["idade"])

    print("\n--- Estatísticas da Clínica ---")
    print(f"Total de pacientes: {total}")
    print(f"Idade média: {media:.1f}")
    print(f"Paciente mais novo: {mais_novo['nome']} ({mais_novo['idade']} anos)")
    print(f"Paciente mais velho: {mais_velho['nome']} ({mais_velho['idade']} anos)")
    print()


def buscar_paciente():
    nome_busca = input("\nDigite o nome do paciente: ").strip().lower()

    encontrados = [p for p in pacientes if nome_busca in p["nome"].lower()]

    if encontrados:
        print("\n--- Resultado da busca ---")
        for p in encontrados:
            print(f"Nome: {p['nome']} | Idade: {p['idade']} | Telefone: {p['telefone']}")
    else:
        print("\nNenhum paciente encontrado com esse nome.")
    print()


def listar_pacientes():
    if not pacientes:
        print("\nNenhum paciente cadastrado.\n")
        return

    print("\n--- Lista de Pacientes ---")
    for i, p in enumerate(pacientes, 1):
        print(f"{i}. Nome: {p['nome']} | Idade: {p['idade']} | Telefone: {p['telefone']}")
    print()


def menu():
    while True:
        print("=== SISTEMA CLÍNICA VIDA+ ===")
        print("1. Cadastrar paciente")
        print("2. Ver estatísticas")
        print("3. Buscar paciente")
        print("4. Listar todos os pacientes")
        print("5. Sair")

        opcao = input("Escolha uma opção: ")

        if opcao == "1":
            cadastrar_paciente()
        elif opcao == "2":
            ver_estatisticas()
        elif opcao == "3":
            buscar_paciente()
        elif opcao == "4":
            listar_pacientes()
        elif opcao == "5":
            print("Encerrando o sistema...")
            break
        else:
            print("Opção inválida. Tente novamente.\n")


menu()
