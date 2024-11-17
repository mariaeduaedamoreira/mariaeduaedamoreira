# tarefa.py
class Tarefa:
    def __init__(self, descricao):
        self.descricao = descricao
        self.concluida = False
    
    def concluir(self):
        self.concluida = True
    
    def excluir(self):
        self.descricao = None
        self.concluida = False

    def __str__(self):
        status = "Concluída" if self.concluida else "Pendente"
        return f"{self.descricao} - {status}"
# main.py
from tarefa import Tarefa

class ListaDeTarefas:
    def __init__(self):
        self.tarefas = []
    
    def adicionar_tarefa(self, descricao):
        nova_tarefa = Tarefa(descricao)
        self.tarefas.append(nova_tarefa)
        print(f"Tarefa '{descricao}' adicionada com sucesso!")
    
    def listar_tarefas(self):
        if not self.tarefas:
            print("Nenhuma tarefa na lista.")
        else:
            for i, tarefa in enumerate(self.tarefas, 1):
                print(f"{i}. {tarefa}")
    
    def concluir_tarefa(self, numero):
        try:
            self.tarefas[numero - 1].concluir()
            print(f"Tarefa {numero} concluída com sucesso!")
        except IndexError:
            print("Tarefa não encontrada.")
    
    def excluir_tarefa(self, numero):
        try:
            tarefa_excluida = self.tarefas.pop(numero - 1)
            print(f"Tarefa '{tarefa_excluida.descricao}' excluída com sucesso!")
        except IndexError:
            print("Tarefa não encontrada.")
    
    def menu(self):
        while True:
            print("\n--- Lista de Tarefas ---")
            print("1. Adicionar Tarefa")
            print("2. Listar Tarefas")
            print("3. Concluir Tarefa")
            print("4. Excluir Tarefa")
            print("5. Sair")
            
            escolha = input("Escolha uma opção: ")
            
            if escolha == '1':
                descricao = input("Digite a descrição da tarefa: ")
                self.adicionar_tarefa(descricao)
            elif escolha == '2':
                self.listar_tarefas()
            elif escolha == '3':
                numero = int(input("Digite o número da tarefa a ser concluída: "))
                self.concluir_tarefa(numero)
            elif escolha == '4':
                numero = int(input("Digite o número da tarefa a ser excluída: "))
                self.excluir_tarefa(numero)
            elif escolha == '5':
                print("Saindo...")
                break
            else:
                print("Opção inválida.")

if __name__ == "__main__":
    lista = ListaDeTarefas()
    lista.menu()
# README.md

# Lista de Tarefas (To-Do List)

## Objetivo
Criar uma aplicação simples de lista de tarefas que permite ao usuário adicionar, listar, concluir e excluir tarefas de forma interativa.

## Funcionalidades
- Adicionar tarefas à lista.
- Listar todas as tarefas com status (Pendente/Concluída).
- Marcar tarefas como concluídas.
- Excluir tarefas da lista.

## Como Executar
1. Clone o repositório.
2. Execute o script `main.py` com o Python 3.x:

   ```bash
   python main.py

