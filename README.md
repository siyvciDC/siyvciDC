from PIL import Image, ImageDraw, ImageFont

def adicionar_texto(imagem, texto, posicao, cor_texto, fonte):
    desenho = ImageDraw.Draw(imagem)
    desenho.text(posicao, texto, fill=cor_texto, font=fonte)

# Caminho para a imagem do designer pronta
caminho_imagem = "caminho_da_sua_imagem.png"

# Carregar a imagem
imagem = Image.open(caminho_imagem)

# Dados do cronograma
cronograma = [
    ("01/08/2023", "Segunda-feira", "9:00", "Bem-vindo à nossa clínica! Conheça a massoterapia."),
    # Insira aqui as demais linhas do cronograma
]

# Configurações de texto
cor_texto = (0, 0, 0)
fonte_titulo = ImageFont.truetype("arial.ttf", 24)
fonte_texto = ImageFont.truetype("arial.ttf", 18)

# Posições das linhas do cronograma na imagem
posicao_y = 50
espaco_linha = 10

# Adicionar as linhas do cronograma à imagem
for data, dia_semana, horario, titulo in cronograma:
    texto_linha = f"{data} - {dia_semana} às {horario}\n{titulo}"
    adicionar_texto(imagem, texto_linha, (50, posicao_y), cor_texto, fonte_titulo)
    posicao_y += fonte_titulo.getsize(texto_linha)[1] + espaco_linha

# Salvar a imagem final
imagem.save("cronograma_com_imagem.png")

print("Imagem do cronograma criada com sucesso!")
