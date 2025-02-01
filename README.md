# BINGO-
Trabalho de programação
import random

def gerar_cartela(modo, jogador):
    
    if modo == 'demorado':
        linhas, colunas = 2, 3
        intervalos = [(1, 10), (11, 20), (21, 30)]
    else:
        linhas, colunas = 3, 4
        intervalos = [(1, 10), (11, 20), (21, 30), (31, 40)]
    cartela = []
    for col in range(colunas):
        numeros_coluna = random.sample(range(intervalos[col][0], intervalos[col][1] + 1), linhas)
        cartela.append(numeros_coluna)
    
    
    cartela = list(map(list, zip(*cartela)))
    return {'jogador': jogador, 'cartela': cartela, 'marcados': set()}

def imprimir_cartela(cartela, sorteados)
    print(f"Cartela de {cartela['jogador']}:")
    for linha in cartela['cartela']:
        for num in linha:
            if num in sorteados:
                print(f"[{num:2}]", end=" ")
            else:
                print(f" {num:2} ", end=" ")
        print()
    print()

def sortear_dezena(sorteados, modo):
    
    if modo == 'rapido':
        intervalo = range(1, 31)
    else:
        intervalo = range(1, 41)
    
    disponiveis = list(set(intervalo) - sorteados)
    return random.choice(disponiveis)


def verificar_vencedor(cartela, sorteados):
    
    return all(num in sorteados for linha in cartela['cartela'] for num in linha)
