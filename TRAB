import random

JOGO = ['''

>>>>>>>>>>JOGO DA FORCA BY: Samuel, Allan e Elton<<<<<<<<<<

+---+
|   |
    |
    |
    |
    |
=========''', '''

+---+
|   |
O   |
    |
    |
    |
=========''', '''

+---+
|   |
O   |
|   |
    |
    |
=========''', '''

 +---+
 |   |
 O   |
/|   |
     |
     |
=========''', '''

 +---+
 |   |
 O   |
/|\  |
     |
     |
=========''', '''

 +---+
 |   |
 O   |
/|\  |
/    |
     |
=========''', '''

 +---+
 |   |
 O   |
/|\  |
/ \  |
     |
=========''']

palavras = 'bola casa massa'.split()
print('JOGO GERADO')


def inicio(): # FUNÇÃO PRINCIPAL QUE INICIA O JOGO #
 
    global JOGO

    print('JOGO DA FORCA')
    letrasErradas = ''
    letrasCertas = ''
    palavraSecreta = geraPalavraAleatoria().upper()

    jogando = True

    while jogando:
        imprimeJogo(letrasErradas, letrasCertas, palavraSecreta)  # ENQUANTO QUISER JOGAR O METODO IMPRIME O GAME #

        if palavraSecreta == "BOLA":  # DICAS PARA AS PALAVRAS #
            print("A dica é: Existe no futebol.") # DICA BOLA #
        elif palavraSecreta == "CASA":
            print("A dica é: Conjunto de Paredes.") # DICA CASA #
        elif palavraSecreta == "MASSA":
            print("A dica é: Peso dos objetos (Conceito Ciências Naturais).") # DICA MASSA #

        chute = recebeChute(
            letrasErradas + letrasCertas)  # VARIAVEL CHUTE VAI RECEBER AS FUNÇÕES DE LETRAS ERRADAS E CERTAS #

        if chute in palavraSecreta:  # SE O CHUTE ESTIVER NA PALAVRA #
            letrasCertas += chute  # INCREMENTA UM EM LETRAS CERTAS #

            if VerificaSeGanhou(palavraSecreta, letrasCertas):  # VERIFICA SE O JOGO FOI VENCIDO #
                print("A palavra secreta é " + palavraSecreta + '! Você ganhou!!') 
                jogando = False # JOGANDO IGUAL FALSO, QUER DIZER QUE O JOGO VAI PARAR #
        else:
            letrasErradas += chute # QUANDO EXCEDEU A QUANTIDADE MÁXIMA DE LETRA #

            if len(letrasErradas) == len( # LEN MOSTRA O TAMANHO DA STRING, OU SEJA, MOSTRA A QUANTIDADE DE LETRAS ERRADAS #
                    JOGO) - 1:  # VERIFICA SE O NUMERO DE LETRAS ERRADAS É IGUAL O NUMERO DE ACERTOS FORCA #
                imprimeJogo(letrasErradas, letrasCertas, palavraSecreta)  # SE SIM CONTINUA IMPRIMINDO O GAME #

                print("Você passou do número permitido de chutes!") # MENSAGEM INFORMANDO QUE O USUÁRIO PERDEU #
                print("Depois de " + str(len(letrasErradas)) + ' letras erradas e ' + str(len(letrasCertas)), end=' ') # MENSAGEM INFORMANDO A QUANTIDADE DE ACERTOS E ERROS #
                print("Chutes certos, a palavra era " + palavraSecreta + '.') # MENSAGEM INFORMANDO A RESPOSTA #

                jogando = False  # JOGANDO IGUAL FALSO, QUER DIZER QUE O JOGO VAI PARAR #

        if not jogando:
            if jogarNovamente(): 
                letrasErradas = ''  # REINICIA LETRAS ERRADAS #
                letrasCertas = ''  # REINICIA LETRAS CERTAS #
                jogando = True # SE O USUÁRIO ESCOLHER SIM, O JOGO REINICIA, OU SEJA, SEMPRE QUE FOR TRUE, O JOGO VAI CONTINUAR #
                palavraSecreta = geraPalavraAleatoria().upper()  # GERA PALAVRA ALEATORIA #


def geraPalavraAleatoria(): # DEFINE A PALAVRA ALEATÓRIAMENTE #
    global palavras
    return random.choice(palavras)


def imprimeComEspacos(palavra): # RECEBE UMA PALAVRA E IMPRIME A MESMA COM ESPAÇO ENTRE AS LETRAS #

    for letra in palavra:
        print(letra, end=' ')

    print()


def imprimeJogo(letrasErradas, letrasCertas, palavraSecreta):
    global JOGO  # DEFINE A VARIAVEL GLOBAL #
    print(JOGO[len(letrasErradas)] + '\n')  # RECEBE QUANTIDADE DE LETRAS ERRADAS #

    print("Letras Erradas:", end=' ')  # PEDINDO LETRAS ERRADAS #
    imprimeComEspacos(letrasErradas)

    vazio = '_' * len(palavraSecreta)  # CRIA ESPAÇO VAZIO #
    for i in range(len(palavraSecreta)): 
        if palavraSecreta[i] in letrasCertas: 
            vazio = vazio[:i] + palavraSecreta[i] + vazio[i + 1:] 

    imprimeComEspacos(vazio)  # CHAMA O METODO DE IMPRESSÃO DE ESPAÇOS VAZIOS #


def recebeChute(chutesFeitos): # FUNÇÃO DE CHUTES DO USUÁRIO #
    while True:
        chute = input("Advinhe alguma letra. \n").upper()

        if len(chute) != 1:
            print("Coloque uma unica letra")
        elif chute in chutesFeitos:  # SE O CHUTE ESTÁ DENTRO DOS CHUTES FEITOS RETORNA O PRINT ABAIXO #
            print("Você já digitou essa letra, digite de novo!")
        elif not 'A' <= chute <= 'Z':  # VERIFICA SE O CHUTE FOI FEITO COM LETRAS E NÃO COM OUTROS CARACTERES #
            print("Permitido somente 1 letra de cada vez e é permitido somente letras!")
        else:
            return chute


def jogarNovamente(): # FUNÇÃO QUE SOLICITA O USUÁRIO SE ELE DESEJA JOGAR NOVAMENTE #

    return input("Você quer jogar novamente? (Sim ou Não)\n").upper().startswith(
        'S')  # SE A RESPOSTA DO USUARIO CONVERTIDO EM MAIUSCULO FOR VERDADEIRO #


def VerificaSeGanhou(palavraSecreta, letrasCertas):
    ganhou = True
    for letra in palavraSecreta:
        if letra not in letrasCertas:
            ganhou = False
            break

    return ganhou


inicio()
