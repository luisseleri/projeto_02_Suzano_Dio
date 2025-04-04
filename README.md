# projeto_02_Suzano_Dio

menu = """

[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> """

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:

    opcao = input(menu)

    if opcao == "d":
      valor = float(input('Informe o valor do depósito: '))

      if valor > 0:
        saldo += valor
        extrato += f'Depósito: {valor:.2f}\n'
      else:
        print('O valor digitado é inválido, refaça a operação')
    
    elif opcao == "s":
      valor = float(input('Informe o valor do saque:'))

      excedeu_saques = numero_saques >= LIMITE_SAQUES #declarar variáveis com as condições para usar no 'if' depois, veja abaixo: 
      excedeu_saldo = valor > saldo
      excedeu_limite = valor > limite  

      if excedeu_saques:
        print('O numero de saques foi excedido')
      if excedeu_saldo:
        print('Você não possui saldo suficiente para poder completar a transação')
      elif excedeu_limite:
        print(f'O limite de transação é de R$500 e você está tentando sacar {valor}')

      elif valor > 0:
        saldo -= valor
        extrato += f"Saque: R$ {valor:.2f}\n"
        numero_saques += 1

      else:
        print('Operação inválida')

    elif opcao == "e":
      print("\n================ EXTRATO ================")
      print("Não foram realizadas movimentações." if not extrato else extrato)
      print(f"\nSaldo: R$ {saldo:.2f}")
      print("==========================================")

       
    elif opcao == "q":
      print('operação finalizada')
      break
        

    else:
        print("Operação inválida, por favor selecione novamente a operação desejada.")
