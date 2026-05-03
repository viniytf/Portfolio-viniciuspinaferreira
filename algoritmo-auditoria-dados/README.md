# 📊 Sistema de Auditoria de Vendas
 
## 📝 Descrição do Projeto
Este projeto consiste em um sistema de auditoria de dados financeiros desenvolvido em Python, com o objetivo de analisar a consistência de vendas e identificar possíveis anomalias.

O algoritmo utiliza média simples, limite de segurança e lógica condicional para detectar discrepâncias (outliers), gerando alertas automáticos para valores suspeitos e auxiliando na validação dos dados.
 
*Figura 1: Execução do sistema com detecção de inconsistências nas vendas.*
 
## 🚀 Tecnologias Utilizadas
* **Linguagem:** Python  
* **Conceitos Aplicados:** Estruturas condicionais, funções, escopo de variáveis e análise de dados  
* **Ferramentas:** VS Code / Terminal
 
## 📊 Funcionalidades
* Cálculo da média de vendas  
* Definição de limite de segurança  
* Identificação de discrepâncias (outliers)  
* Geração de alertas automáticos para revisão manual

  ## 💻 Código do Projeto

<details>
<summary>📂 Clique para ver o código</summary>

```python
LIMITE_SEGURANCA = 10000.0

v1 = float(input("Venda 1: "))
v2 = float(input("Venda 2: "))
v3 = float(input("Venda 3: "))

def analisar_vendas(v1, v2, v3):
    global LIMITE_SEGURANCA

    media = (v1 + v2 + v3) / 3
    print("Média:", media)

    if media > LIMITE_SEGURANCA:
        print("SISTEMA EM QUARENTENA")

    if v1 > media * 5 or v2 > media * 5 or v3 > media * 5:
        print("REVISÃO MANUAL")

    print("Tipo v1:", type(v1))
    print("Tipo média:", type(media))
    print("Tipo limite:", type(LIMITE_SEGURANCA))

analisar_vendas(v1, v2, v3)
 
## 🔧 Como Executar
1. Clone o repositório.  
2. Acesse a pasta do projeto.  
3. Execute o comando:  
```bash
python nome_do_arquivo.py
