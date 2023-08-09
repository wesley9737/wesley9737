# Meu Projeto Incrível

Bem-vindo ao meu projeto incrível! Este é um espaço onde compartilho minhas ideias e trabalho duro. Sinta-se à vontade para explorar, contribuir e dar feedback.

## Sobre

Este projeto visa resolver [descreva o problema que o projeto aborda]. Utilizei [linguagem/tecnologia/framework] para construir esta solução.

## Como Contribuir

Se você quiser contribuir para este projeto, siga estas etapas:

1. Faça um fork deste repositório.
2. Crie um novo branch com sua modificação: `git checkout -b minha-modificacao`
3. Faça suas alterações e commit: `git commit -m 'Adicionei uma nova funcionalidade'`
4. Envie para o branch remoto: `git push origin minha-modificacao`
5. Abra um Pull Request!

## Contato

Você pode me encontrar em [LinkedIn](https://www.linkedin.com/in/wesley-scolaro-32648917b) ou [Whatsapp](https://wa.me/554197371327).

## Licença

Este projeto está licenciado sob a [Nome da Licença]. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.
def print_tabuleiro(tabuleiro):
    for linha in tabuleiro:
        print(" | ".join(linha))
        print("-" * 9)

def verificar_vitoria(tabuleiro, jogador):
    for linha in tabuleiro:
        if all(c == jogador for c in linha):
            return True

    for coluna in range(3):
        if all(tabuleiro[linha][coluna] == jogador for linha in range(3)):
            return True

    if all(tabuleiro[i][i] == jogador for i in range(3)) or all(tabuleiro[i][2 - i] == jogador for i in range(3)):
        return True

    return False

def jogo_da_velha():
    tabuleiro = [[" " for _ in range(3)] for _ in range(3)]
    jogador_atual = "X"
    
    while True:
        print_tabuleiro(tabuleiro)
        linha = int(input(f"Jogador {jogador_atual}, escolha a linha (0, 1, 2): "))
        coluna = int(input(f"Jogador {jogador_atual}, escolha a coluna (0, 1, 2): "))
        
        if tabuleiro[linha][coluna] == " ":
            tabuleiro[linha][coluna] = jogador_atual
            if verificar_vitoria(tabuleiro, jogador_atual):
                print_tabuleiro(tabuleiro)
                print(f"Jogador {jogador_atual} venceu!")
                break
            jogador_atual = "O" if jogador_atual == "X" else "X"
        else:
            print("Essa posição já está ocupada. Escolha outra.")

if __name__ == "__main__":
    jogo_da_velha()
