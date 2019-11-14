# program

agenda = []

def pede_nome():
     return(input("Nome: "))

def pede_telefone():
     return(input("Telefone: "))

def mostra_dados(nome, telefone):
     print("Nome: %s Telefone: %s" % (nome, telefone))

def pede_nome_arquivo():
     return(input("Nome do arquivo: "))

def pesquisa(nome):
     mnome = nome.lower()
     for p, e in enumerate(agenda):
         if e[0].lower() == mnome:
               return p
     return None

def novo():
     global agenda
     nome = pede_nome()
     telefone = pede_telefone()
     agenda.append([nome, telefone])

def apaga():
     global agenda
     nome = pede_nome()
     p = pesquisa(nome)
     if p != None:
         del agenda[p]
     else:
         print("Nome não encontrado.")

def altera():
     p = pesquisa(pede_nome())
     if p != None:
         nome = agenda[p][0]
         telefone = agenda[p][1]
         print("Encontrado:")
         mostra_dados(nome, telefone)
         nome = pede_nome()
         telefone = pede_telefone()
         agenda[p] = [nome, telefone]
     else:
         print("Nome não encontrado.")

def lista():
     print("\nAgenda\n\n------")
     for e in agenda:
         mostra_dados(e[0], e[1])
     print("------\n")


def valida_faixa_inteiro(pergunta, inicio, fim):
     while True:
         try:
               valor = int(input(pergunta))
               if inicio <= valor <= fim:
                   return(valor)
         except ValueError:
               print("Valor inválido, favor digitar entre %d e %d" % (inicio, fim))

def menu():
     print("""
   1 - Novo
   2 - Altera
   3 - Apaga
   4 - Lista
   
   0 - Sai
""")
     return valida_faixa_inteiro("Escolha uma opção: ",0,4)

while True:
     opção = menu()
     if opção == 0:
         break
     elif opção == 1:
         novo()
     elif opção == 2:
         altera()
     elif opção == 3:
         apaga()
     elif opção == 4:
         lista()
