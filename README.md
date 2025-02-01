8# BINGO-
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

def main():
    print("Bem-vindo ao Simulador de Bingo!")
    
    
    modo = input("Escolha o modo (Escreva: rapido ou demorado): ").strip().lower()
    while modo not in ['rapido', 'demorado']:
        print("Modo inválido. Escolha 'rapido' ou 'demorado'.")
        modo = input("Escolha o modo (rapido/demorado): ").strip().lower()
    
    
    if modo == 'rapido':
        jogadores = ['Jogador 1', 'Jogador 2']
    else:
        jogadores = ['Jogador 1', 'Jogador 2', 'Jogador 3', 'Jogador 4']
    
    
    cartelas = [gerar_cartela(modo, jogador) for jogador in jogadores]
    sorteados = set()
    vencedores = []

while True:
        
        if len(sorteados) == (30 if modo == 'rapido' else 40):
            print("Todas as dezenas foram sorteadas. Fim de jogo!")
            break
        
        
        dezena = sortear_dezena(sorteados, modo)
        sorteados.add(dezena)
        print(f"Última dezena sorteada: {dezena}")
        print(f"Dezenas sorteadas até agora: {sorted(sorteados)}")
        
        
        for cartela in cartelas:
            if dezena in [num for linha in cartela['cartela'] for num in linha]:
                cartela['marcados'].add(dezena)
            imprimir_cartela(cartela, sorteados)
        
        
        for cartela in cartelas:
            if verificar_vencedor(cartela, sorteados):
                if cartela['jogador'] not in vencedores:
                    vencedores.append(cartela['jogador'])
        
        
        if vencedores:
            print(f"Parabéns aos vencedores: {', '.join(vencedores)}")
            break
        
        
        input("Pressione Enter para sortear a próxima dezena...")

if __name__ == "__main__":
    main()

