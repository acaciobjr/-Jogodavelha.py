# -Jogodavelha.py
programa criado para fim acadêmico.


table = [['_','_','_'],['_','_','_'],['_','_','_']]
historicoTab = []
winner = []
ganhar = False
jogador1 = "X"
jogador2 = "O"


def escolherOpcaoEOrientar():
    print()
    print('===============================')
    print('|            MENU             |')
    print('===============================')
    print('|PARA JOGAR DIGITE 1          |')
    print()
    print('|PARA VER O HISTÓRICO DIGITE 2|')
    print()
    print("|PARA VOLTAR AO MENU DIGITE 3 |")
    print('===============================')
    opcao = int(input("      Digite sua opção: "))

    while opcao != 3:
        if opcao == 1:
            limparTabuleiro()
            jogar()
            
        
        if opcao == 2:
            mostrarHistorico()


        if opcao ==  3:
          print("Fim do jogo!")


        print()
        print('PARA JOGAR DIGITE 1 ')
        print()
        print('PARA VER O HISTÓRICO DIGITE 2')
        print()
        print("PARA VOLTAR AO MENU DIGITE 3")
        print()
        opcao = int(input("Digite sua opção: "))



def jogar():
    
    while(True):
        mostrarTabuleiro()
        inserirLinhaColuna(jogador1)

        if(checarSeGanhou(jogador1) == True):
            break
            
        mostrarTabuleiro()
        inserirLinhaColuna(jogador2)

        if(checarSeGanhou(jogador2) == True):
            break



def mostrarTabuleiro():
    print('-------------------------JOGO DA VELHA-------------------------')
    for i in range(0,3):
        print()
        print('                         ',
              table[i][0],'|', table[i][1],'|', table[i][2])
    print()



def inserirLinhaColuna(jogador):
    linha1 = int(input('JOGADOR '+ jogador+' | DIGITE A LINHA: '))
    coluna1 = int (input('JOGADOR '+ jogador+' | DIGITE A COLUNA: '))
    print()

    table[linha1 - 1][coluna1 - 1] = jogador



def limparTabuleiro():
    for i in range(0,3):
        for j in range(0,3):
            table[i][j] = '_'



def mostrarHistorico():
    numeroDePartidas = len(historicoTab)
    for a in range(0,numeroDePartidas):
        print('-------------------------PARTIDA----------------------------------'.format(a+1))
        print(winner[a])
        for l in range(0,3):
            print('')
            print ('                         ',
                     historicoTab[a][l][0],'|', historicoTab[a][l][1],'|', historicoTab[a][l][2])
            print()



def checarSeGanhou(jogador):
    velha = darVelha()
    linha =ganharEmLinha()
    coluna = ganharEmColuna()
    diagonal = ganharEmDiagonal()

    if(velha == True or linha == True or coluna == True or diagonal == True):
        mostrarTabuleiro()
        historicoTab.append(table)
        return True

        

def ganharEmLinha():
    for a in range (0,3):
        if table[a][0] == 'X' and table[a][1] == 'X' and table[a][2] == 'X':
            print('Jogador 1 Ganhou!')
            winner.append("jogador 1 ganhou!")
            return True
            
        if table[a][0] == 'O' and table[a][1] == 'O' and table[a][2]== 'O':
            print('Jogador 2 Ganhou!')
            winner.append("jogador 2 ganhou!")
            return True
        
    return False



def ganharEmColuna():
    for k in range (0,3):
        if table[0][k] == 'X' and table[1][k] == 'X' and table[2][k] == 'X' :
            print('Jogador 1 Ganhou!')
            winner.append("jogador 1 ganhou!")
            return True
                  
        if table[0][k] == 'O' and table[1][k] == 'O' and table[2][k] == 'O' :
            print('Jogador 2 Ganhou!')
            winner.append("jogador 2 ganhou!")            
            return True
    return False



def ganharEmDiagonal():
    if table[0][0]== 'X' and table[1][1]== 'X' and table[2][2] == 'X':
        print ('Jogador 1 Ganhou!')
        winner.append("jogador 1 ganhou!")
        return True
          
    if table[0][2]== 'X' and table[1][1]== 'X' and table[2][0] == 'X':
        print ('Jogador 1 Ganhou!')
        winner.append("jogador 1 ganhou!")
        return True
                  
    if table[0][0]== 'O' and table[1][1]== 'O' and table[2][2] == "O":
        print ('Jogador 2 Ganhou!')
        winner.append("jogador 2 ganhou!")
        return True
          
    if table[0][2] == 'O' and table[1][1] == 'O' and table[2][0] == 'O':
        print('Jogador 2 Ganhou!')
        winner.append("jogador 2 ganhou!")
        return True

    return False



def darVelha():
    if (table[0][0] != '_' and table[0][1] != '_'and table[0][2] != '_'):
        if(table[1][0] != '_' and table[1][1] != '_' and table[1][2] != '_'):
            if (table[2][0] != '_' and table[2][1] != '_' and table[2][2] != '_'):
                if (ganharEmLinha() == False and ganharEmColuna() == False and ganharEmDiagonal() == False):
                    print ("# Deu velha #")
                    winner.append("Velha")
                    return True
    return False



escolherOpcaoEOrientar()
