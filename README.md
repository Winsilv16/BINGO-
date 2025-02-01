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
    