import random
import time

def jogar_caca_niqueis():
    saldo = 1000  
    print("Bem-vindo ao Meu Cassino Virtual!")
    print("Seu saldo inicial é de R$", saldo)
    
    while True:
        print("\n1 - Jogar caça-níqueis")
        print("2 - Sair")
        escolha = input("Escolha uma opção: ")
        
        if escolha == "1":
            aposta = int(input("Quanto você quer apostar? R$"))
            if aposta > saldo:
                print("Saldo insuficiente para essa aposta!")
                continue
            
            
            print("\nGirando... 🎰")
            time.sleep(2)
            resultados = [random.choice(["🍒", "🍋", "🔔", "💎", "7️⃣"]) for _ in range(3)]
            print("Resultado:", " | ".join(resultados))
            
            # Checa os resultados
            if len(set(resultados)) == 1:  
                ganho = aposta * 5
                saldo += ganho
                print("Jackpot! Parabéns! Você ganhou R$", ganho)
            elif len(set(resultados)) == 2:  
                ganho = aposta * 2
                saldo += ganho
                print("Você ganhou R$", ganho)
            else:
                saldo -= aposta
                print("Você perdeu R$", aposta)
            
            print("Seu saldo atual é de R$", saldo)
            if saldo <= 0:
                print("Seu saldo estáesgotado! O jogo terminou.")
                break
        
        elif escolha == "2":
            print("Saindo do cassino... Até a próxima!")
            break
        else:
            print("Opção inválida! Tente novamente.")


jogar_caca_niqueis()
