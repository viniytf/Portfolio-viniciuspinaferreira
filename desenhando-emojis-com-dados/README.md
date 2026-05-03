# 🎨 Desenhando Emojis com Dados
 
## 📝 Descrição do Projeto
Este projeto utiliza estruturas de dados como matrizes, dicionários e tuplas para criar representações visuais em forma de arte pixelada, além de manipular dados musicais e imagens utilizando lógica de programação.

A proposta combina conceitos de programação com visualização gráfica utilizando a biblioteca matplotlib.
 
## 🚀 Tecnologias Utilizadas
* **Linguagem:** Python  
* **Bibliotecas:** Matplotlib  
* **Conceitos Aplicados:** Matrizes, listas aninhadas, dicionários, tuplas, loops aninhados e transposição de matrizes  
* **Ferramentas:** VS Code / Google Colab
 
## 📊 Funcionalidades
* Criação de emoji em pixel utilizando matriz  
* Visualização gráfica com matplotlib  
* Manipulação de dados musicais com dicionários  
* Transposição manual de matrizes  
* Gerenciamento de lista de imagens (playlist visual)  

---

## 💻 Código do Projeto

<details>
<summary>📂 Clique para ver todo o código</summary>

```python
# ==========================================
# 🎨 PARTE 1 — Criação de Emoji com Matriz
# Função: gerar imagem pixelada com matplotlib
# ==========================================

import matplotlib.pyplot as plt

emoji_data = {
  "nome": "Smile",
  "grade": [
    [(255,255,0), (255,255,0), (255,255,0), (255,255,0), (255,255,0)],
    [(255,255,0), (0,0,0),  (255,255,0), (0,0,0),  (255,255,0)],
    [(255,255,0), (255,255,0), (255,255,0), (255,255,0), (255,255,0)],
    [(255,255,0), (0,0,0),  (0,0,0),  (0,0,0),  (255,255,0)],
    [(255,255,0), (255,255,0), (255,255,0), (255,255,0), (255,255,0)]
  ]
}

plt.imshow(emoji_data["grade"])
plt.title("Emoji Pixel Art")
plt.show()


# ==========================================
# 🎵 PARTE 2 — Manipulação de Dados Musicais
# Função: transposição de matriz de frequência
# ==========================================

biblioteca_musical = {
  "Toques": [
    {"Alegre": ([440, 480], [520, 560])},
    {"Triste": ([200, 150], [100, 50])}
  ]
}

for chave, lista_toques in biblioteca_musical.items():
  for musica in lista_toques:
    for nome, matriz in musica.items():
      print(f"Música: {nome}")
      print("Antes:", list(matriz))

      transposta = [
        [matriz[0][0], matriz[1][0]],
        [matriz[0][1], matriz[1][1]]
      ]

      for linha in transposta:
        print(" linha transposta:", linha)

      musica.update({nome: transposta})
      print("Depois:", musica[nome])


# ==========================================
# 🖼️ PARTE 3 — Manipulação de Playlist Visual
# Função: gerenciar imagens com listas e dicionários
# ==========================================

playlist = {
  "nome": "Minha Playlist",
  "imagens": [
    {
      "titulo": "Sol",
      "pixels": (
        (255, 200, 0),
        (255, 220, 50),
        (200, 150, 0)
      )
    },
    {
      "titulo": "Céu",
      "pixels": (
        (100, 150, 255),
        (50, 100, 200),
        (30, 80, 180)
      )
    },
    {
      "titulo": "Grama",
      "pixels": (
        (0, 180, 50),
        (0, 140, 30),
        (50, 200, 80)
      )
    }
  ]
}

nova_imagem = {"titulo": "Fogo", "pixels": ((255,80,0), (255,40,0), (200,20,0))}
playlist["imagens"].insert(0, nova_imagem)

removida = playlist["imagens"].pop()
print(f"Imagem removida: {removida['titulo']}")

for chave in playlist.keys():
  if chave == "imagens":
    for imagem in playlist[chave]:
      print(f"Imagem: {imagem['titulo']}")
      for pixel in imagem["pixels"]:
        print(f"  pixel: {pixel}")
