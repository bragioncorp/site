---
title: "Computação Gráfica - Resumão para P1"
excerpt: "Resumo Computação Gráfica"
categories:
  - Computação Gráfica
tags:
  - Computação Gráfica
  - Resumo
  - Teoria
  - Processamento de Imagem
  - Análise de Imagem
  - Síntse de Imagem

toc: true
---

# Abertura da matéria

Computação Gráfica → 3 grandes áreas

![image](https://github.com/user-attachments/assets/00d10566-a32e-475a-bce9-3af59d072f75)

## Processamento de imagem

Área mais pesquisada e evoluída.  
Imagem que entra é alguma foto e precisa ser complexa → digitalização.  
Ajuda a preparar as imagens que serão analisadas (imagem mais critica).  

- Procura o tratamento e alterações de imagens digitais.  
- O objetivo é fazer modificações em imagens digitais para se obterem outras imagens digitais.  
- Engloba qualquer aplicação de edição de imagens com processamentos de filtragem, segmentação e reconstrução.  

## Análise de imagem

Imagem processada entra aqui.  
Questões mais simples.  
Resulta em dados para a síntese.  

- Objetivo é extrair características e análise de dados extraídos da imagem que foi digitalizada.  
- Para isso, a imagem digital pode passar por pré-processamento, visando facilitar a extração de características.  
- Pode ser uma filtragem, com o objetivo de realçar características, ou uma segmentação, com o objetivo de separar objetos de interesse.

## Síntese de imagem

Área mais antiga e conhecida.  
Desenhar alguma coisa com os dados recebidos.  
Gerar uma imagem e retorna ao processamento de imagem  → renderização.  

- Procura à produção de imagens sintéticas a partir de modelos matemáticos e transformações do modelo.  
- Também trata da criação de interfaces gráficas de usuário e animações.  
- A imagem digital é o produto final resultante de processamentos realizados sobre modelos e descritores de imagem.

## Observações

- Imagem externa para processamento → digitalização.
- Imagem da síntese para processamento → renderização.

Ex: Entrar com dados (foto de uma casa - digitalização), processar (filtros), analisar (obter a posição das janelas) e devolver uma imagem (janelas em 3D pelo Blender, por exemplo -> renderização).

## Por fim

Imagem que entra do mundo externo - digitalizada.  
Imagem sintetizado - sintética / vetorial.  

# Aula I

![image](https://github.com/user-attachments/assets/e4ec7326-15a3-41a1-b04d-54b86ea6d558)

## Realidade concreta

É o que vivemos, o que podemos tocar.  
Ex: placa, ler o que está escrito no livro, copo de vidro...  

Consguimos extrair informação (conjunto) de algo que existe.  

## Realidade virtual

Substitui as informações que a realidade concreta (real) estaria entregando.  
O observador sabe que não é concreta.  
Ex: Óculos para enxergar, fone de ouvido para ouvir, esteira para andar e outros equipamentos para traduzir sentidos reais no virtual e vice-versa.  

## Realidade misturada

No meio dos dois.  
Não se encaixa nem em virtual e nem em concreta.  

### Elementos mais proximos do real - realidade aumentada

Aumento as informações da realidade concreta (real).  
Ex: ao pesquisar "cachorro" no google, você consegue projetar um cachorro na vida real usando a câmera, ao simular na superfie plana.  

Mistura de coisas que existem no ambiente real (móvel, iluminação) acrescidas da informação virtual (cachorro).  
Junção entre elementos reais e elementos virtuais - predominância de elementos reais.  

Ex 2: Pokemon Go
![image](https://github.com/user-attachments/assets/7f2c7991-1879-4ab5-86bc-8084e8715655)

### Elementos mais proximos do virtual - virtualidade aumentada

Também é uma junção do real e virtual.  
Muito mais elementos virtuais do que reais.  

É o que acontece com filme ou jornal com apresentador usando fundo verde com outra imagem para dar a impressão que está em outro lugar.

Ex: Jornal Nacional
![image](https://github.com/user-attachments/assets/90e4eb1c-8bc3-4dee-8f2f-29d89e8f1ce7)

## Resumindo

Realidade virtual -> muitos equipamentos/periféricos para existir.  

Realidade aumentada -> precisa apenas de webcam e computador para existir.

## Hoje em dia

Realidade aumentada de forma muito simples - próprio google.  

Realidade virtual - ainda que seja uma tecnologia evoluída, principalmente no mundo do entretenimento (compra de alguns dos periféricos), os equipamento são restritos (caros e necesistam de mais processamento).

## Linha crescente

Da realidade concreta para realidade virtual.  
Aumentando a quantidade de elementos virtuais apresentadas ao observador.  

A observação das diferentes realidades pode ser continua.  

> A realidade virtual da década de 90 é a realidade virtual imersiva atual.  

## Realidade virtual imersiva

Para que a pessoa experimentar, são necessários equipamentos que traduzam todos os sentidos para o ambiente virtual.  
Tato, olfato, visão, audição e rosto traduzidos de alguma maneira.  
Objetivo de simular sensações como se fossem provenientes da realidade concreta.

Ex: Jogador Número 1
![image](https://github.com/user-attachments/assets/4703ac12-6824-49c1-b526-13a7165a39ef)

## Realidade virtual não imersiva

Muito presente em jogos - vai te transportar para uma outra realidade.  
Imersivo de maneira contemporânea sem todos os aparelhos.  
Não considera os outros sentidos - como tato e olfato.

Ex: Beat Saber
![image](https://github.com/user-attachments/assets/40ac7c36-236b-4554-9dd5-a50295aa8227)

## Fundamentos de imagem - Cap II

A imagem é uma representação visual ou gráfica de um objeto, cena, pessoa ou conceito.  
São formas poderosas de comunicação e expressão visual que podem transmitir informações, emoções e ideias.

Imagem digital ou matricial -> resultado do processo de digitalização e é uma matriz de valores chamados pixels.  

Possuem 3 canais para armazenar as cores R, G e B.

![image](https://github.com/user-attachments/assets/99f93269-f378-4c12-8222-6d0898cbcfc1)

A imagem representada por uma matriz é chamada de imagem matricial, bitmap ou, simplesmente, imagem digital.

![image](https://github.com/user-attachments/assets/7dc00ddc-5cc9-4c28-8661-e9c0933de5c0)

## Cones e bastonetes

![image](https://github.com/user-attachments/assets/68ad4198-ddd9-4d20-be66-5c4bf36cbf30)

Os cones e bastonetes são células fotossensíveis localizadas na retina dos olhos e são responsáveis pela percepção da luz e cores.

- Cones: responsáveis pela visão em cores (RGB) e existem três tipos de cones, cada um sensível a uma das três cores primárias: vermelho, verde e azul. Eles funcionam melhor em condições de luz intensa.

- Bastonetes: responsáveis pela percepção de preto e branco, ou seja, pela visão em tons de cinza. Eles são mais sensíveis à luz do que os cones e funcionam melhor em condições de pouca luz, mas não distinguem cores.

## Digitalização

![image](https://github.com/user-attachments/assets/32a6714c-da24-4de3-bb1a-8f8f4052ec4e)

Etapas de digitalização

### Sinal original

Fótons da realidade concreta saindo da lâmpada, refletindo no objeto e as informações luminosas chegando no olho (cones e bastonetes).  

### Fitro analógico

Relacionados com qualidade da máquina fotografia.  
Os sensores vão perceber a quantidade de fótons chegando (sensores mais precisos conseguem perceber uma maior quantidade de luz e vice-versa).  
Imagem capturada pela câmera gera o sinal filtrado.  

### Sinal filtrado

Já é menor que o original, possui menos informações.  

### Amostragem

Quantidade de quadradrihos eu vou subdividir esses sinal filtrado.  
Representa os pixels da minha imagem final.  
Quanto mais amostras, melhor a resolução.  

Resulta sinal amostrado.  

Ex: 2 mega pixels = 2 milhões de quadradinhos que "olham" o sinal filtrado e tentam representar o comportamento do mesmo.  
Diretamente relacionado com a quantidade de pixels que eu vou ter lá no final da minha imagem.  
Quanto mais amostragem, melhor a resolução da imagem.  

### Sinal amostrado

A quantidade de elementos que eu vou escolher para representar o sinal original a partir do sinal filtrado.  

### Quantização

Atribuição de valores a cada uma dessas amostras.  
Recebe 3 valores, 256 tonalidades de R G e B, 8 bits para cada um dos canais.  
Para representar 1 core - 1 bit só (imagem binárioa).  

Quanto menos bits, mais informações perdidas.  
Quanto mais eu aumentar, mais bits na grade de quantização, maior a capacidade de representação da imagem.  

Resulta no sinal digital.  

### Sinal digital
Sinal já digitalizado.  

### Sistema digital
Faz o armazenamento da imagem digital (sinal digital) no sistema para uso futuro.  

### Sinal digital
Disponivel para os todos dispositivos.  

## Observação

### Amostragem
É o processo de geração de amostras (medição) para cada pedaço do conteúdo filtrado (analógico). O intervalo entre as amostras é determinado por um pulso de sincronismo e a sua frequência é chamada de taxa de amostragem.

### Quantização
É o processo de definição do tamanho (quanto vai pesar) de cada amostra coletada. Atribuí um valor binário que representa a amplitude da amostra.

![image](https://github.com/user-attachments/assets/20718faf-a57d-4140-bbf6-fdde17be63df)

![image](https://github.com/user-attachments/assets/d2e84ba8-9141-45d1-940e-c8d80a0ded88)

## Pontos positivos e negativos da digitalização

Positivos  

- Manipulação,
- Armazenamento,
- Distribuição.

negativos  

- Nível de detable (menos informações).

## Bitmap e imagens vetoriais

Uma imagem pode ser totalmente descrita por equações vetoriais, ou melhor dizendo, por meio de descritores de imagens, para ser desenhada apenas quando necessário.  

Imagens descritas com base neste princípio são chamadas imagens vetoriais

Bitmap é diferente de vetorial.  
Vetorial -> função matematica.  

Depois de ser digitalizada -> matrizes bitmap (.bmp).

## RGB e CMY

O modelo RGB surgiu através de estudos de composição de luzes e demonstraram que a partir de apenas três cores primárias é possível obter todas as outras cores do espectro da luz visível.

As três cores primárias que apresentam as melhores combinações para gerar outras cores são as cores vermelho (Red), verde (Green) e azul (Blue), dando origem ao modelo RGB.

![image](https://github.com/user-attachments/assets/698ded06-a315-4b77-946d-e4ab4c7bb19c)

O modelo RGB é um modelo de cor aditivo e a combinação das cores primárias gera as cores secundárias.  

Com r = 0, não há contribuição da cor vermelha, e com r = 255, há o máximo de contribuição da cor vermelha. O mesmo vale para as cores verde (g) e azul (b).  

Uma cor é, portanto, um ponto no interior do cubo RGB, cujos vértices representam:  

- as cores primárias (R, G e B),
- as cores secundárias (C, M e Y),
- a ausência de cor (K),
- a composição de todas as cores (W).  

![image](https://github.com/user-attachments/assets/84872c5e-448e-41c7-b6e1-1f3c92eaa927)

## HSL

HSL (Hue, Saturation, Lightness) é um modelo de cores que representa as cores de forma mais próxima à percepção humana, onde a matiz define a tonalidade (como vermelho ou azul), a saturação define a intensidade da cor, e a luminosidade define a quantidade de luz.

Diferente do RGB (Red, Green, Blue), que mistura as três cores primárias em diferentes intensidades para criar outras cores, o HSL separa a cor em aspectos que são mais intuitivos para manipulação, como ajustar a intensidade ou a claridade de uma cor específica.

Ex: clarear uma cor em HSL envolve simplesmente aumentar o valor da luminosidade, enquanto no RGB é necessário um cálculo mais complexo, podendo alterar inadvertidamente a tonalidade da cor.

Obs:  
O contradomínio da componente luminância (L) do HSL contém todos os contornos da imagem (como uma fotografia monocromática) e possui a relação de ordem (número inteiro). 

![image](https://github.com/user-attachments/assets/174ae2e8-cd1f-4516-b582-cfafbf13f4e1)

# Aula II

## Representação de imagems

Área mais essencial da imagem (juntamente com os fundamentos - aula passada).

Com a maior capacidade de processamento, houve a evolução e o aumentado da representação do objeto - se aproximando da realidade (comparação dos gráficos de ps1 com ps5).

Vértices ligados 2 a 2 formam arestas.  
Arestas ligadas 3 a 3 formam faces.  

2 algorítmos em especial.  

## Criando imagem com Opencv no Python

Criar uma imagem com 3 canais (canais de cores).

```
color=np.ones((200,200,3))*155
```

![image](https://github.com/user-attachments/assets/7fc08138-ee9f-46b1-b70d-4c1f791d4c15)

Preenchidas com 1 - multiplicou por 155

## Criando retas com Opencv no Python

Parâmetros: (matriz, inicio, final, cor, espessura)

```
color=cv2.line(color,(0,0),(200,200),(17,200,180),4)
```

![image](https://github.com/user-attachments/assets/9a826ffa-cf2a-4ace-ab65-eccaad06c39a)


## Criando círculos com Opencv no Python

Cria a imagem 200 por 200 com 3 canais.  
Desenhando um círculo vermelho com o centro em (100, 100) e raio 50, cor e espessura são os outros dois parametros

```
image2 = np.zeros((200, 200, 3))
image2 = cv2.circle(image2, (100, 100), 50, (5, 0, 200), 2)
```

![image](https://github.com/user-attachments/assets/1c5a1029-ba67-479c-aaaf-2c988969e6c9)


## Exercíco 1
Criar uma paisagem com as funções de retas e círculos.

Utilize as funções de linhas e de círculos para desenvolver uma composição (em uma imagem matricial) que apresente um cenário no qual se observam:

- um gramado
- uma árvore
- montanhas
- o céu
- o por-do-sol

```
paisagem = np.zeros((200, 200, 3))

paisagem = cv2.line(paisagem,(0,0),(200,0),(120, 80, 0), 320) #ceu

for i in range(0, 25):
  paisagem = cv2.circle(paisagem, (200, 160), i, (0, 255, 255), 2) # sol

paisagem = cv2.line(paisagem,(2,180),(200,180),(120, 220, 120), 35) # grama

paisagem = cv2.line(paisagem,(50,140),(50,170),(0, 120, 200), 9) # arvore
for i in range(0, 25):
    paisagem = cv2.circle(paisagem, (50, 120), i, (0, 255, 0), 2) # folha

# montanha 1
paisagem = cv2.line(paisagem,(90,170),(110,130),(42, 77, 107), 2)
paisagem = cv2.line(paisagem,(130,170),(110,130),(42, 77, 107), 2)
paisagem = cv2.line(paisagem,(90,170),(130,170),(42, 77, 107), 2)

pts = np.array([[90, 170], [110, 130], [130, 170]], np.int32)
pts = pts.reshape((-1, 1, 2))

cv2.fillPoly(paisagem, [pts], (42, 77, 107))

# montanha 2
paisagem = cv2.line(paisagem,(130,170),(140,90),(42, 77, 107), 2)
paisagem = cv2.line(paisagem,(140,90),(170,170),(42, 77, 107), 2)
paisagem = cv2.line(paisagem,(90,170),(170,170),(42, 77, 107), 2)

pts = np.array([[130,170], [140,90], [170,170]], np.int32)
pts = pts.reshape((-1, 1, 2))

cv2.fillPoly(paisagem, [pts], (42, 77, 107))

# nuvem 1 e 2
for i in range(0, 15):
    paisagem = cv2.circle(paisagem, (50, 30), i, (255, 255, 255), 2) # folha
    paisagem = cv2.circle(paisagem, (60, 30), i, (255, 255, 255), 2) # folha
    paisagem = cv2.circle(paisagem, (70, 30), i, (255, 255, 255), 2) # folha

    paisagem = cv2.circle(paisagem, (140, 40), i, (255, 255, 255), 2) # folha
    paisagem = cv2.circle(paisagem, (150, 40), i, (255, 255, 255), 2) # folha
    paisagem = cv2.circle(paisagem, (160, 40), i, (255, 255, 255), 2) # folha

cv2_imshow(paisagem)
```

![image](https://github.com/user-attachments/assets/ac52e58b-a722-4883-8fe7-7bf09dd1978a)

## Algoritmos

## Algoritmo DDA

Desenha retas muitos bem feitas, porém utiliza elementos que vão fazer com que perca um pouco de tempo (divisões e arredondamentos).

Dificuldade maior para realizar desenho em tempo real - quando precisa interagir com objetos.  

Ex: jogo - entrando com informações em tempo real - DDA demora muito (principalmente quando usar funções externas).  

```
#algoritmo DDA

#definindo a função DDA
def dda(x1, y1, x2, y2):
  #calculando a diferença entre os pontos
  dx = x2 - x1
  dy = y2 - y1

  #calculando os passos
  if abs(dx) > abs(dy):
    steps = abs(dx)
  else:
    steps = abs(dy)

  #calculando o incremento
  x_increment = dx / steps
  y_increment = dy / steps

  x = x1
  y = y1

  pixels = []

  #percorrendo os passos
  for _ in range(steps):
    #adicionando o pixel na lista
    pixels.append((round(x), round(y)))
    #calculando o próximo pixel
    x += x_increment
    y += y_increment

  #retornando a lista de pixels
  return pixels
```

## Exercício 2

Obter entradas do usuário e criar um triângulo com o algoritmo DDA.

```
triangulo = np.zeros((200, 200))

x1 = int(input("Valor X1: "))
y1 = int(input("Valor Y1: "))
x2 = int(input("Valor X2: "))
y2 = int(input("Valor Y2: "))
x3 = int(input("Valor X3: "))
y3 = int(input("Valor Y3: "))

a = dda(x1, y1, x2, y2)
b = dda(x3, y3, x2, y2)
c = dda(x1, y1, x3, y3)

vertices = a + b + c
for pixel in vertices:
  x, y = pixel
  triangulo[y, x] = 255

cv2_imshow(triangulo)
```

![image](https://github.com/user-attachments/assets/650b385b-cd83-4b75-a5d7-17fd7b3e83fc)

## Observação

Hoje em dia com o poder de processamento avançado várias chamadas são feitas em pontos próximos para maior definição.  

Ex: várias chamdas de Bresenham para o desenho de um círculo. 

## Algoritmo Bresenham para Retas

Evolução do DDA - para desenhar mais rápido.  

Evita fazer contas de dividir e arredondamento. 

Verifica se pixel próximo é um pixel à direta ou um pixel na diagonal subindo com base em 1 ou -1.

```
#algoritmo de Bresenham

def bresenham(x1, y1, x2, y2):
    dx = abs(x2 - x1)
    dy = abs(y2 - y1)
    sx = 1 if x1 < x2 else -1
    sy = 1 if y1 < y2 else -1
    err = dx - dy

    pixels = []
    while True:
        pixels.append((x1, y1))
        if x1 == x2 and y1 == y2:
            break
        e2 = 2 * err
        if e2 > -dy:
            err -= dy
            x1 += sx
        if e2 < dx:
            err += dx
            y1 += sy

    return pixels
```

## Exercício 3

Demonstre na prática que o algoritmo Bresenham é mais rápido que o algoritmo DDA.

```
import time

image3 = np.zeros((200, 200))

x1 = int(input("Valor X1: "))
y1 = int(input("Valor Y1: "))
x2 = int(input("Valor X2: "))
y2 = int(input("Valor Y2: "))

start_time = time.time()

dda_pix = dda(x1, y1, x2, y2)
for pixel in dda_pix:
    x, y = pixel
    image3[y, x] = 255

end_time = time.time()

execution_time = end_time - start_time

cv2_imshow(image3)
print(f"DDA: {execution_time:.5f} segundos")

start_time = time.time()

bre_pix = bresenham(x1, y1, x2, y2)
for pixel in bre_pix:
    x, y = pixel
    image3[y, x] = 255

end_time = time.time()

execution_time = end_time - start_time

cv2_imshow(image3)
print(f"Bresenham: {execution_time:.5f} segundos")
```

![image](https://github.com/user-attachments/assets/e6fedc7e-a51b-4366-b529-1031613fd8ec)

# Aula III

## Como é feito o desenho de cículos?

Calcular só alguns pixels do círculo, os outros são obtidos por espelhamento: 360 dividido por 8 octantes.  
Algoritmo de círculo deve calcular apenas um octante e os outros s~s~o encontrados por espelhamento.  

Isso economiza processamento e poder computacional.  

Quanto menos pixels para representação, mais torto o círculo vai ficar.  

![image](https://github.com/user-attachments/assets/f70642ab-2489-40eb-9eb1-38f65347e94a)

![image](https://github.com/user-attachments/assets/4bf3259f-1914-4339-98e9-82b57f4c7cd6)

## Algoritmo Bresenham para Círculos

Sem divisão e sem arredondamento.  
X começa maior que y.  

## Processamento de Imagem

Recebe uma imagem (matriz) de entrada - resulta imagem (matriz) melhorada com alguma manipulação.  

Estar em tom de cinza não significa necessariamente que a imagem possui apenas 1 canal, ela pode estar entregando dois canais extras a toa.  

É necessário transformar os 3 canais em 1 canal para que as transformações sejam mais rapidas (não precisa passar os 3 canais).  
- A maioria das manipulações vão usar em imagens de tons de cinza (0 a 255).  
- As operações morfológica usam imagens binárias (1 ou 0).  

### Domínio Espacial

A imagem é trabalhada diretamente em termos de pixels e suas intensidades. Processos como filtros e operações de convolução utilizam kernels (ou máscaras), que são pequenos blocos de pixels usados para modificar a imagem.

Ex: um kernel de desfoque pode ser aplicado a cada pixel da imagem para suavizar os detalhes.

### Domínio da Frequência

As imagens são analisadas em termos de suas componentes de frequência. A transformação de Fourier é usada para converter a imagem do domínio espacial para o domínio da frequência.

Nesse domínio, filtros são aplicados para modificar a imagem. Ao aplicar um filtro no domínio da frequência e depois transformar de volta para o domínio espacial, você pode realizar operações como remoção de ruído ou aumento de contraste.

### Imagem usada

![image](https://github.com/user-attachments/assets/bdfa8bd9-438d-4926-b28b-b7f34cd33c62)

## Operações pontuais

Também conhecida como operações de ponto.

Tratam cada pixel de uma imagem de forma independente, ou seja, a operação aplicada a um pixel não depende dos valores dos pixels vizinhos.

Essas operações são aplicadas diretamente à intensidade ou cor de cada pixel, baseando-se apenas nos próprios valores do pixel.

### Conversão de cor (tons de cinza)

```
cinza=cv2.cvtColor(img,cv2.COLOR_BGR2GRAY)
```

![image](https://github.com/user-attachments/assets/86f7db30-1f5d-4c6a-80c5-b4ac9e0c0bd2)

### Binarização

Transforma uma imagem em tons de cinza para 2 pontos, ou seja, de 255 tons de cinza para 0 e 1.  

Contornos mais chamativos/proeminentes são guardadas.  
Forma mais barata de representar uma imagem (de 8 bit por pixel para 1 bit por pixel).  

Preto, branco e mistura de preto e branco custam o mesmo poder computacional.  

A forma binarizada é a mais barata possivel e a mais inteligente entre as baratas.  

Parâmetros: matriz, limiar, para qual vai converter e função.

```
ret,binaria = cv2.threshold(cinza,100,255,cv2.THRESH_BINARY)
```

![image](https://github.com/user-attachments/assets/51d07312-cc8f-4a10-916c-df02796417e7)

OBS: 'ret' armazena o erro no retorn o (caso tenha) e 'binaria' armazena o resultado.

### Por que ao diminuir o limiar eu aumento a qntdade de brancos?

Pois 0-50 é preto e 51-255 é branco, então terá mais branco, ou seja, maior possibilidade de branco do que preto.

### Limiarização

Diminuir a quantidade de tons em uma imagem.  
Diferentes limiares.  

## Operações de contexto

Também chamadas de operações de vizinhança.  

Consideram o valor de um pixel em relação aos valores dos pixels vizinhos.

Essas operações são fundamentais para processos de filtragem, detecção de bordas, suavização e outros efeitos que dependem do padrão local de pixels.

### Filtro de Média

Famoso blur.

Suavização de contornos.  
Kernel é o espaço que será selecionado para realizar a operação.

O pixel resultante é muito distante da imagem original.

Quanto maior o kernel:
- mais destruida será a imagem
- maior será a diversidade dos pixels vizinhos
- mais tempo de processamento vai ser consumido.

```
imgBlur = cv2.blur(cinza,(10,10))
```

![image](https://github.com/user-attachments/assets/8254e436-a0af-406e-a83a-fe9e87b4317b)

### Filtro de Mediana

Suavização para remover ruídos.

Método mais longo e caro.  

Percorre a imagem, usa um kernel que vai selecionar um pedacinho dessa imagem, depois fazer a ordenação e por fim a criação da imagem resultante.  

Imagens maiores -> muito mais ordenação de vetores -> mais demorado.

```
imgMedian = cv2.medianBlur(cinza,3)
```

Neste caso o kernel só pode ser **ímpar**.

![image](https://github.com/user-attachments/assets/0f557874-9d9e-4f00-899f-bab03af53055)

### Filtro Gaussiano

Passa baixa.  

Perde para o filtro de média.  
Não gera efeitos indesejáveis nas bordas como o filtro de média.  

Conserva um pouco mais da informação original.  
Para kernels do mesmo tamanho, o filtro gaussiano tem o comportamento melhor.

Suaviza contornos com menor perda.

```
imgGauss = cv2.GaussianBlur(cinza,(3,3),0)
```

![image](https://github.com/user-attachments/assets/4056c3b6-e48e-43f7-a66a-55fcf13802b5)

### Filtro Canny

Vai encontrar as bordas.  

Filtro passa alta.  
Se for passado em imagem ruidosa, fica mto ruim.

A imagem ruidosa deve passar primeiro pelo filtro passa baixa (remover ruídos) e depois para passa alta (encontrar bordas ou fazer outra transformação).

Define dois limiares e detecta as bordas entre estes dois limiares.  

```
t_lower = 50  # Lower Threshold
t_upper = 150  # Upper threshold

edge = cv2.Canny(cinza, t_lower, t_upper)
```

![image](https://github.com/user-attachments/assets/79877fa1-8267-49c3-8789-a65f80d0438d)

### Filtro manual (customizado)

Define um kernel manual para a operações.

Detector de borda:  
Pixel central mais forte

```
kernel = np.array([[-1, -1, -1],
                   [-1,  8, -1],
                   [-1, -1, -1]])
```

Laplaciano:  
Identiifca bordas de maneira mais suave.  
Central mais suave e eixos X sem valor.  

```
kernel2 = np.array([[0, -1, 0],
                   [-1,  4, -1],
                   [0, -1, 0]])
```

Identidade:  
Considera o peso do pixel central.  
Deixa imagem mais clara.  

```
kernel3 = np.array([[0, 0, 0],
                   [0,  1, 0],
                   [0, 0, 0]])
```

Aplicar o filtro com o kernel.

```
imagem = cv2.filter2D(imgMedian, -1, kernel2)
```

![image](https://github.com/user-attachments/assets/2113718c-7561-4bed-856f-74f65ccd1b05)
![image](https://github.com/user-attachments/assets/931a8cfa-5f92-4ba9-b463-a10f5f2967da)
![image](https://github.com/user-attachments/assets/2b60fa64-5580-4843-8292-697989914946)


## Extra

Adição de brilho, contraste, subtração do pixel, soma de duas imagens, subtração de duas imagens.  

setosa.io/ev/image-kernel.  

Este site mostra os calculos feitos pelo blur.  

Formação classica do filtro gaussiano.  

Filtro gaussiano também chamado de filtro de media ponderada.  

## Histogramas

Mostra o espalhamento dos tons claros, cinza ou escuros em uma imagem.  

```
hist = cv2.calcHist(imgMedian,[0],None,[256],[0,256])
```

Tipos:
- Histograma muito concentrado no centro: imagem com baixo constraste, muito tons de cinza médio.  
- Histograma com alta concentração no inicio: imagem muito escura, precisa melhorar o contraste.  
- Histograma com alta no final: imagem muito branca, precisa melhorar contraste.  

O objetivo é encontrar o espalhamento homogêneo dos pixels, ou seja, encontrar o histograma equalizado.  

```
imgEq = cv2.equalizeHist(imgMedian)
```

### Histograma Original

![image](https://github.com/user-attachments/assets/841260a5-3eaa-471d-95ff-20e8840491e5)

### Histograma Ajustado

![image](https://github.com/user-attachments/assets/b2ab88d2-9ca3-4331-8c5f-3d66c5c51031)

### Imagem Original e Ajustada

![image](https://github.com/user-attachments/assets/85e384a7-036a-4d19-926f-bc5040288766)


### Eficiência
Essa representação é MENOS EFICIENTE do que uma representação que reconstrói e ordena os pixels.  

Percorrer histograma é MAIS FÁCIL que percorrer matriz, pois é um vetor que guarda poucas informações da imagem.  
As operações sobre histogramas tendem a ser mais rapida, e quando possivel, usar histograma pela agilidade.  

Encontra o resultado de maneira eficiente utilizando pouco poder comptuacional.  

Ex: transformo a imagem em histograma e comparo no banco de dados para verificar de fomra mais rápida se existe algum semelhante. Recupero e faço as operações de forma ágil, computacionalmente muito eficiente.  

# Aula IV

## Operações Morfológicas

São técnicas de processamento de imagens que se baseiam na forma e na estrutura dos objetos dentro de uma imagem.  

Usadas em imagens preto e branco.

## Erosão

Crescimento das regiões de preto em áreas brancas (remoção de ruído branco).  

Pega valores em preto e aumenta.  
Objetivo eliminação de ruidos brancas em áreas pretas.  

Reduzir pixels brancos e aumentar pixels pretos.  

![image](https://github.com/user-attachments/assets/7ad77a69-7f81-4bd5-a019-a1d1711ad889)

## Dilatação

Crescimento das regiões em branco em áres pretas.  

Remoção de ruído preto.  

![image](https://github.com/user-attachments/assets/daac40e8-890f-44df-bbdc-79ba6cc8aaa4)

## Abertura e fechamento

São tipos esspecíficos de erosão e dilação.

## Abertura

A abertura é composta por uma erosão seguida de dilatação.

Conservação dos elementos estruturias e filtra de ruidos brancos em fundos pretos.

![image](https://github.com/user-attachments/assets/4cc2cc2b-fc07-4f51-818d-23bd3b7ea0b5)

## Fechamento

O fechamento é o contrário da abertura.  
Uma dilatação seguida de erosão.  

Há uma tentativa de conservação dos elementos estruturais - ainda da para reconhecer.

![image](https://github.com/user-attachments/assets/40b7108c-4cf6-42b8-8d62-1e9f4f045d8f)
