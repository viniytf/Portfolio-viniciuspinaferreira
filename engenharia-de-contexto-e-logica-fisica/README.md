# 🌆 Engenharia de Contexto e Lógica Física
 
## 📝 Descrição do Projeto
Este projeto aplica conceitos de lógica de programação para análise de microclima urbano e simulação de evacuação em ambientes reais.

A solução utiliza dados ambientais e estruturas lógicas para interpretar condições climáticas e simular tomada de decisão em situações críticas.
 
## 🚀 Tecnologias Utilizadas
* **Linguagem:** Python  
* **Conceitos Aplicados:** Listas aninhadas, loops duplos, match-case, estruturas condicionais e modelagem lógica  
* **Ferramentas:** VS Code / Google Colab
 
## 📊 Funcionalidades
* Análise de microclima urbano em diferentes regiões  
* Classificação da qualidade do ar (IQA)  
* Cálculo de conforto urbano  
* Simulação de evacuação com tomada de decisão dinâmica  

---

## 💻 Código do Projeto

<details>
<summary>📂 Clique para ver todos os códigos</summary>

```python
# ==========================================
# 🌡️ PARTE 1 — Análise de Microclima Urbano
# Função: analisa temperatura, umidade e IQA
# ==========================================

dados_locais = [
  ["Praça Metrô Itaquera", 17, 82, 38, 27, 32, 72],
  ["Cruzamento Radial/Aricanduva", 18, 78, 65, 28, 30, 95],
  ["UNICID - Vila Carrão", 17, 80, 42, 26, 34, 58],
]

HORARIOS = ["Manhã (07h)", "Tarde (14h)"]

def classificar_iqa(iqa: int) -> str:
  match True:
    case _ if iqa <= 40:
      return "✅ Boa"
    case _ if iqa <= 80:
      return "🟡 Moderada"
    case _ if iqa <= 120:
      return "🟠 Ruim"
    case _ if iqa <= 200:
      return "🔴 Muito Ruim"
    case _:
      return "⛔ Péssima"

def calcular_nota_conforto(temp: float, umid: float, iqa: int) -> float:
  nota_temp = 10 - min(10, abs(temp - 21) * 0.7)
  nota_umid = 10 - min(10, abs(umid - 60) * 0.15)
  nota_iqa = 10 - min(10, iqa * 0.05)

  nota_final = (nota_temp * 0.35) + (nota_umid * 0.25) + (nota_iqa * 0.40)
  return round(nota_final, 2)

def analisar_microclima():
  print("=" * 60)
  print(" ANÁLISE DE MICROCLIMA")
  print("=" * 60)

  for local in dados_locais:
    nome_local = local[0]
    print(f"\n📍 LOCAL: {nome_local}")
    print("-" * 50)

    medicoes = [
      (local[1], local[2], local[3]),
      (local[4], local[5], local[6]),
    ]

    for i, (temp, umid, iqa) in enumerate(medicoes):
      horario = HORARIOS[i]

      print(f"\n ⏰ {horario}")
      print(f"  • Temperatura: {temp}°C")
      print(f"  • Umidade: {umid}%")
      print(f"  • IQA: {iqa} → {classificar_iqa(iqa)}")

      nota = calcular_nota_conforto(temp, umid, iqa)
      print(f"  ⭐ Nota de Conforto: {nota}/10")

analisar_microclima()


# ==========================================
# 🚨 PARTE 2 — Simulador de Evacuação
# Função: simula tomada de decisão em rota
# ==========================================

locais = [
  "Sala de Aula (1º Andar)",
  "Porta da Sala",
  "Corredor",
  "Escada",
  "Saída do Bloco",
  "Rua",
]

estados = [
  "livre",
  "porta_travada",
  "livre",
  "escada_estreita",
  "porta_corta_fogo",
  "saida",
]

agente = {"posicao": 0, "energia": 100, "chave": True, "historico": []}

def registrar(msg):
  agente["historico"].append(msg)
  print(msg)

def simular_evacuacao():
  print("🚨 Iniciando evacuação\n")

  while agente["energia"] > 0:
    pos = agente["posicao"]
    estado = estados[pos]

    print(f"\n📍 {locais[pos]} | Energia: {agente['energia']}")

    if estado == "saida":
      registrar("Evacuação concluída!")
      break

    if estado == "livre":
      agente["posicao"] += 1
      agente["energia"] -= 5

    elif estado == "porta_travada":
      if agente["chave"]:
        agente["posicao"] += 1
        agente["energia"] -= 10
      else:
        agente["energia"] -= 10

    elif estado == "escada_estreita":
      agente["posicao"] += 1
      agente["energia"] -= 20

    elif estado == "porta_corta_fogo":
      agente["posicao"] += 1
      agente["energia"] -= 15

simular_evacuacao()
