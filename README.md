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
