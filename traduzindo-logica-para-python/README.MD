# 🧠 Traduzindo Lógica para Python
 
## 📝 Descrição do Projeto
Este projeto reúne quatro programas desenvolvidos em Python com o objetivo de aplicar conceitos fundamentais de lógica de programação na prática.

Os sistemas incluem processamento de vendas, análise de clima, gestão de notas e simulação de investimentos, abordando diferentes cenários do mundo real.
 
## 🚀 Tecnologias Utilizadas
* **Linguagem:** Python  
* **Conceitos Aplicados:** Funções, loops, condicionais, tipagem e conversão de dados  
* **Ferramentas:** VS Code / Terminal
 
## 📊 Funcionalidades
* Processamento de vendas com aplicação de descontos  
* Análise de temperaturas semanais  
* Sistema de notas de alunos  
* Simulação de poupança com juros compostos  

---

## 💻 Código do Projeto

<details>
<summary>📂 Clique para ver todos os códigos</summary>

```python
# ================================
# 🛒 Código 1 — Processador de Vendas com Desconto
# Função: calcula o total da compra e aplica descontos
# ================================

def processar_vendas():
    total_compra = 0.0
    itens_comprados = 0

    quantidade_tipos = int(input("Quantos produtos diferentes foram comprados? "))

    contador = 0
    while contador < quantidade_tipos:
        nome = input("Nome do produto: ")
        preco = float(input("Preço unitário: "))
        qtd = int(input(f"Quantidade de '{nome}': "))

        if preco <= 0 or qtd <= 0:
            print(f"Valores inválidos para '{nome}'. Item ignorado.")
        else:
            subtotal = preco * qtd
            total_compra += subtotal
            itens_comprados += qtd

        contador += 1

    if total_compra > 500:
        total_final = total_compra * 0.90
        print("Desconto de 10% aplicado!")
    elif total_compra > 200:
        total_final = total_compra * 0.95
        print("Desconto de 5% aplicado!")
    else:
        total_final = total_compra

    print(f"\nResumo: {itens_comprados} itens. Total a pagar: R$ {total_final:.2f}")

processar_vendas()


# ================================
# 🌡️ Código 2 — Analisador de Clima Semanal
# Função: calcula média semanal e detecta temperaturas extremas
# ================================

def analisar_clima():
    soma_temperaturas = 0.0
    dias_quentes = 0
    alerta_extremo = False

    dia = 1
    while dia <= 7:
        temp = float(input(f"Digite a temperatura do dia {dia}: "))
        soma_temperaturas += temp

        if temp > 35.0:
            dias_quentes += 1

        if temp > 45.0 or temp < -5.0:
            alerta_extremo = True

        dia += 1

    media = soma_temperaturas / 7
    print("Média semanal:", media)
    print("Dias acima de 35°C:", dias_quentes)

    if alerta_extremo:
        print("CUIDADO: Condições climáticas perigosas detectadas!")
    else:
        print("Clima dentro da normalidade operacional.")

analisar_clima()


# ================================
# 🎓 Código 3 — Sistema de Notas da Turma
# Função: calcula média dos alunos e classifica desempenho
# ================================

def sistema_notas_turma():
    total_alunos = int(input("Quantos alunos existem na turma? "))

    contador = 1
    while contador <= total_alunos:
        aluno_nome = input("Nome do aluno: ")
        n1 = float(input("Nota 1: "))
        n2 = float(input("Nota 2: "))

        media_aluno = (n1 + n2) / 2

        if media_aluno >= 7.0:
            print(aluno_nome, ": Aprovado com média", media_aluno)
        elif media_aluno >= 5.0:
            print(aluno_nome, ": Recuperação (Média:", media_aluno, ")")
        else:
            print(aluno_nome, ": Reprovado")

        contador += 1

sistema_notas_turma()


# ================================
# 💰 Código 4 — Simulador de Poupança
# Função: simula investimento com juros compostos
# ================================

def simulador_poupanca():
    saldo = float(input("Valor inicial do investimento: "))
    taxa = float(input("Taxa de juros mensal (em %): "))
    meses = int(input("Número de meses da simulação: "))

    m = 1
    while m <= meses:
        aporte = float(input(f"Quanto deseja depositar no mês {m}? (0 para nenhum) "))

        saldo += aporte
        juros = saldo * (taxa / 100)
        saldo += juros

        print("Mês", m, ": Saldo atualizado = R$", saldo)

        if saldo > 10000.0:
            print("Parabéns! Você atingiu a meta de 10k no mês", m)

        m += 1

    print("Resultado final após", meses, "meses: R$", saldo)

simulador_poupanca()
