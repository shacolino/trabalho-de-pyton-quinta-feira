class Conta:
    def __init__(self, numero, titular, saldo, tipo_conta):
        self.numero = numero
        self.titular = titular
        self.saldo = saldo
        self.tipo_conta = tipo_conta

    def sacar(self, valor):
        if valor > self.saldo:
            print("Saldo insuficiente!")
            return False
        else:
            self.saldo -= valor
            return True

    def depositar(self, valor):
        self.saldo += valor

    def imprimir_titular(self):
        print(f"Titular: {self.titular}")

    def obter_saldo(self):
        return self.saldo

    def transferir(self, valor, conta_destino):
        if self.sacar(valor):
            conta_destino.depositar(valor)
            print(f"Transferido {valor} para {conta_destino.titular}")
        else:
            print("Transferência não realizada. Saldo insuficiente.")

    def obter_tipo_conta(self):
        return self.tipo_conta

# Exemplo de uso:
conta1 = Conta(1, "João", 1000.0, "Corrente")
conta2 = Conta(2, "Maria", 500.0, "Poupança")

conta1.imprimir_titular()
print("Saldo:", conta1.obter_saldo())
conta1.sacar(150)
print("Saldo após saque:", conta1.obter_saldo())
conta1.depositar(200)
print("Saldo após depósito:", conta1.obter_saldo())
conta1.transferir(300, conta2)
print("Saldo conta1:", conta1.obter_saldo())
print("Saldo conta2:", conta2.obter_saldo())
print("Tipo de conta:", conta1.obter_tipo_conta())
