---
title: "Computação Gráfica - Resumão para P2"
excerpt: "Resumo Computação Gráfica"
categories:
  - Computação Gráfica
tags:
  - Computação Gráfica
  - Resumo
  - Teoria
  - Transformações Geométricas

toc: true
---

# Aula VI

Transformações mais simples: escala e translação.

## Escala

A Figura abaixo mostra a transformação de escala de quatro pontos: (2,1), (3,1), (2,2), (3,2). A escala aplicada foi de três vezes, no eixo x, e quatro vezes, no eixo y: (sx,sy)=(3,4).

![image](https://github.com/user-attachments/assets/aa02c3df-102b-4954-b856-ae7e341fbeb7)

### 2D

Forma direta:

x2 = sx * x1  
y2 = sy * y1  

Forma de matriz:  

![image](https://github.com/user-attachments/assets/a531beee-3b10-49b5-be06-5142561e8051)

### 3D

Forma direta:

x2 = sx * x1  
y2 = sy * y1  
z2 = z1

Forma de matriz:

![image](https://github.com/user-attachments/assets/1473971f-1e44-45e7-a77a-a97c4f13c474)

## Translação

A Figura abaixo representa por uma seta a translação do ponto (x1,y1)=(3,2) de (tx, ty) = (3,6), levando-o para o ponto (x2,y2)=(6,8).

![image](https://github.com/user-attachments/assets/00a459c5-2250-4b56-a3d2-fc19f022ae5c)

### 2D

Forma direta:

x2 = tx + x1  
y2 = ty + y1  

### 3D

Forma direta:

x2 = tx + x1  
y2 = ty + y1  
z2 = tz + z1

Forma de matriz:

![image](https://github.com/user-attachments/assets/c461bea7-2787-4b73-8126-4a29e5e94c05)

## Matrizes resultantes - escala e translação:

![image](https://github.com/user-attachments/assets/a70db3e1-6be8-4b24-aa40-63fac7cc0376)

## Rotação

A rotação de um ponto bidimensional (x1 ,x2) por um ângulo α em torno da origem é representada na figura abaixo.

![image](https://github.com/user-attachments/assets/00f7de29-0e09-488e-8b52-470edc29d881)

### 2D

Matriz de rotação

![image](https://github.com/user-attachments/assets/a77e62b0-7e52-48eb-abb5-9dc53b65c932)

### 3D

A matriz R pode ser facilmente estendida para três dimensões para as rotações em torno de um dos três eixos. Por ser uma rotação em torno do eixo Z, a coordenada Z não é alterada. A matriz de rotação é igual à matriz 2D, apenas acrescida da dimensão Z.

![image](https://github.com/user-attachments/assets/1f6eee19-54b6-4ebc-94ef-9748df11e74c)

Da qual podemos derivar Rxα e Ryα de rotação em torno dos eixos X e Y, respectivamente.

![image](https://github.com/user-attachments/assets/d1cf729c-bdc2-4f5a-b2c4-288f052396c4)

## Rotação no próprio eixo (centro fora da origem)

A rotação bidimensional em torno de um centro fora da origem pode ser obtida pela composição de transformações. A figura abaixo ilustra a rotação em torno do ponto c=(xc,yc).

![image](https://github.com/user-attachments/assets/28f6736a-2420-41f7-84ef-416e479aa53d)

- Fazer a translação de –c, de forma que o ponto c fique coincidente com a origem;
- Fazer a rotação pela matriz Rα , em torno da origem;
- Fazer a translação de c, de forma que o ponto c volte ao lugar correto.

![image](https://github.com/user-attachments/assets/7c0a4de0-43e7-433f-a706-dbdbf7026854)

![image](https://github.com/user-attachments/assets/c0b21151-385e-4edd-929d-da47493d9e7d)

# Aula VII

## Síntese de imagem

Recebe dados como entrada (da análise de imagem).

A imagem apresentada pelo processo de síntese é diferente da imagem que entrou no processo (amostragem, digitalização).

Na síntese os mesmos pontos da imagem podem originar outros objetos.

A ideia da imagem gerada da síntese é uma imagem descrita por um conjunto de informações (diz ao sistema como vai criar a outra imagem).

## Onde é aplicada?

Aplicações de síntese em CG são muito pesquisadas e aprimoradas.

Isso pois recebem muita grana e existem muitas industriais que se desenvolvem a partir da síntese.

Duas áreas/aplicações proeminentes são:

- Jogos
- Animações

Ex 1 - Jogo Tomb Raider:

![image](https://github.com/user-attachments/assets/b914dac8-2a9a-41e3-bd18-9f0f14a84cd3)

Ex 2 - Filme Toy Story:

![image](https://github.com/user-attachments/assets/ad8ac53c-dec2-4b2e-ab6b-66de55d5a87d)

Estas imagens também servem para mostrar como a área de síntese foi rapidamente aprimorada com o passar do tempo.

Jogos antigos possuíam poucos conjuntos de vértices, resultando em esferas mais "quadradas" -> menos polígonos.

> Polígonos = dados inseridos no ambiente.

Quanto mais quantidades de faces (dados), mais realista o jogo fica (Tomb Raider 2023).

A evolução também é graças à capacidade de processamento melhorada -> o computador consegue entender grande quantidade de vértices e depois renderizar imagens mais complexas.

Além disso, consigo fazer outras coisas nesta mesma área.  
Ex: produção de arquitetura, modelar em 2D ou 3D, etc...

Ex 3 - Blender:

![image](https://github.com/user-attachments/assets/010c9678-5271-44b9-a3bd-898a06c8346b)

## Síntese para jogos VS síntese para animações

### Filmes/Animações

Elementos não interativos -> tendem a ser mais fotorrealista porque os elementos estão estáticos e sem mudanças, sendo melhores para uma renderização mais realista.

### Jogos

Elementos interativos -> menos realista que os filmes porque a renderização precisa ser calculada dependendo da escolha do jogador.

### Observação

Muitos algoritmos para a renderização são aplicados às Engines de jogos na tentativa de deixar o jogo o mais realista possível.

Ex 4 - Unity

![image](https://github.com/user-attachments/assets/608b0b66-416f-461d-801c-a133be261e6e)

Ex 5 - Unreal

![image](https://github.com/user-attachments/assets/1025536b-890f-4d67-80a0-d9f3429d51b8)

A indústria de jogos também vai se inspirar nos algoritmos realistas de filmes/animações.
  
Os filmes também vão se inspiram nos melhores algoritmos de jogos.

> Um ajuda o outro.

## Artefatos da síntese de imagem

![image](https://github.com/user-attachments/assets/f60bc24d-c1f9-437d-85ed-ad8a220d9158)

- Modelo matemático: descreve o mundo real.

- Descrição: cria uma representação detalhada da imagem baseada no modelo matemático.

- Descritor de imagem: conjunto de dados que caracteriza a imagem, podendo ser transformado ou manipulado.

- Transformações: aplicação de operações geométricas (como rotação, translação, escalonamento) sobre o descritor de imagem.

- Serialização: conversão do descritor de imagem em um formato que possa ser armazenado ou transmitido.

- Arquivo Descritor de Imagem: guarda o descritor de imagem serializado em um arquivo que só pode ser aberto pelo editor (Blender, Photoshop, Maya...) - tem acesso aos objeto e as alterações feitas quando aberto.

- Digitalização: ou renderização (diferente da digitalização já estudada), converte o descritor de imagem em dados digitais que podem ser processados para gerar uma imagem final (é o pipeline).

- Imagem Digital: representação final em formato digital pronta para exibição.

- Exibição: mostra a imagem digital na Tela

- Tela: Periférico conectado à GPU onde exibe a imagem.

## O que é Pipeline Tradicional de Visualização?

Também chamado de pipeline de renderização, é o processo de vários estágios em que a saída de um estágio é a entrada do próximo na sequência.

O pipeline tradicional de visualização converte dados geométricos e de cena em uma imagem final exibida na tela.

![image](https://github.com/user-attachments/assets/2f03ff6f-a4d4-4717-aed1-288c76850aad)

## Explique os itens da aplicação

A aplicação representa a interface inicial, onde o usuário fornece:

- Dados de Iluminação: informações sobre as fontes de luz, usadas para calcular como a iluminação afetará as cores e sombras na cena.

- Pontos de Vista: define o ângulo, a posição de visualização da câmera, a quantidada de câmeras ou do observador na cena.

- Vértices de Malhas Poligonais: posições dos pontos (vértices) que compõem os polígonos, definem a geometria dos objetos.

- Malhas Poligonais: conjunto de polígonos que formam a superfície dos objetos na cena.

- Dados de Cor e Textura: informações visuais aplicadas às malhas, determinam a aparência de cor e textura dos objetos.

## Explique os itens do pipeline

### Transformações geométricas

Aplicadas aos vértices das próprias malhas.
 
Processos que aplicam translações, rotações e escalonamentos aos objetos (malhas), ajustando sua posição e orientação na cena.

### Digitalização

Projeção (transformação) de perspectiva de pontos e gera diversos fragmentos de imagem digital para preparação na exibição.

Converte o spaço contínuo para espaço discreto, ou seja, gera pixels.

Leva em consideração a existência de oclusões.

### Montagem

Combina os fragmentos e realiza ajustes finais para criar a imagem completa, levando em consideração sobreposição e opacidade.

### Tela

Periférico conectado à GPU onde exibe a imagem.

> Obs: a realimentação em várias etapas permite ajustes em tempo real, atualizando os dados com base em mudanças ou entrada do usuário.

## Onde o pipeline fica no diagrama de síntese?

![image](https://github.com/user-attachments/assets/48ea9981-1f6b-4acf-a585-996618415e5c)

## Para que serve a entrada de usuário no pipeline?

Permite a interação com o modelo 3D, modificando cenas ou alterando a posição e direcionamento de câmeras virtuais (pontos de vistas).

A entrada de usuário junto com a realimentação de informações de estágios do pipeline permite a criação de animações interativas.

Ex: rotacionar a câmera para visualizar o objeto 3D no Blender enquanto renderiza o objeto na tela.

## O que OpenGL e Direct3D?

São APIs (Application Programming Interfaces) de desenvolvimento que implementam tarefas e até mesmo todo o pipeline gráfico, podendo utilizar recursos disponíveis em hardware nas unidades de processamento gráfico (GPUs).

OpenGL é a versão multiplataforma e Direct3D é específica para Windows.

## Defina o estágio de renderização

Fase do pipeline onde os dados processados da cena (como geometria, iluminação e textura) são convertidos em pixels para formar a imagem final exibida na tela.

Pode incluir técnicas como rasterização, ray tracing ou ray casting para gerar a imagem final.

# Aula VIII

## Como projetar recursos 3D na tela do computador/celucar?

Síntese de imagem -> pipeline de visualização -> ray casting / tay tracing.

## O que é Ray Casting?

![image](https://upload.wikimedia.org/wikipedia/commons/e/e7/Simple_raycasting_with_fisheye_correction.gif)

![image](https://repository-images.githubusercontent.com/274744093/4e2fbf00-b922-11ea-946b-58b5beda91be)

- Algoritmo mais clássico e mais interessante que foi descoberto para a construção de imagens 2D.

- Etapa onde a imagem do campo de visão da cãmera (FOV) será renderizada e apresentada ao espectador.

- Determina quais objetos da cena são visíveis a partir de uma câmera, projetando "raios" da câmera para identificar interseções com objetos. Se este raio tocar em alguma superfície, o pixel no local (tela) receberá a mesma cor do objeto - gera fragmentos de imagem e representa o plano de visualização.

- Limita a quantidade de processamento do número de pixels da imagem (objetos complexos), tornando a renderização viável a computação.

![image](https://github.com/user-attachments/assets/679d0101-fdcc-4c29-8bf3-0ec4c1bc8758)

> Não interpreta objetos transparentes.

**PROBLEMA**: caso a imagem seja bem detalhada (muito realista), o tamanho de armazenamento vai ser bem grande.

## Seria possível a câmera caputurar ao infinito?

A câmera não vai capturar ao infinito graças ao seu campo de visão.

Se for um campo grande, vai capturar uma grande área.

Se for um campo pequeno, vai capturar uma pequena área.

![image](https://github.com/user-attachments/assets/d2e98f3b-d221-4c94-b70c-13001d62f9e4)

## Para que servem as Normais?

A normal serve para o algoritmo de Ray Casting saber o que renderizar e exibir para o apresentador, economizando recursos e tempo.

![image](https://github.com/user-attachments/assets/18f174c5-5213-407b-a23d-4d59a61b75bd)

Geralmente em jogos, as normais dos mapas estão apenas para cima, tanto que se você entrar no mapa, não verá nada.

Sem as normais, eu precisaria considerar a outra face durante a renderização.

## O que é uma face difusa?

É uma face / material que não é muito reflexivo.

Ex: o couro.

## Qual é a diferença para Ray Tracing?

Ray Casting: não considera a interação dos objetos em cena e não considera a composição de cores misturada com a luz (que pode gerar uma nova cor).

Ray Tracing: Considera as fontes de luz com os pixels vizinhos, e com isso, há a combinação de cores, devolvendo um aspecto mais real.

![raytracing1](https://www.pixelsham.com/wp-content/uploads/2019/10/ray_tracing_2.jpg)

![raytracing2](https://www.pixelsham.com/wp-content/uploads/2019/10/rasterization-vs-raytracing-l.jpg)

# Aula 9

Apresentação grupos.

## Modelo geométrico

Representação geométrica dos objetos tridimensionais.

Permite que objetos e cenários sejam representados digitalmente, manipulados e visualizados de diferentes ângulos e perspectivas.

Diferentes formas de representar a estrutura e a superfície de objetos no espaço tridimensional.

### Modelos baseados em poligonos

Polígonos que se conectam por vértices e arestas.

Permite a criação de formas complexas de maneira eficiente, possibilitando que artistas e desenvolvedores manipulem e animem objetos em ambientes tridimensionais.

Necessidade de otimização para garantir o desempenho em tempo real.

![image](https://github.com/user-attachments/assets/d02ea4ae-974b-4bb2-9fcb-90168cd0563c)

### Modelos baseados em malhas

Tipo de polígono tridimensional que utiliza uma rede de vértices, arestas e faces para formar a superfície de um objeto.

Polígonos conectados que definem a forma e a topologia do modelo -> criação de geometria complexas.

Necessita controle detalhado sobre a geometria e a otimização para garantir uma performance adequada em tempo real.

A qualidade da malha pode impactar diretamente a aparência do modelo em renderizações e animações, exigindo que artistas e desenvolvedores equilibrem complexidade geométrica e eficiência.

![image](https://github.com/user-attachments/assets/36cda923-8b5a-498f-aad6-d75de952f002)

### Modelos baseados em voxels

Voxels = grade de cubos (ou "voxels") para criar objetos e ambientes, um valor em uma grade tridimensional, funcionando como o equivalente 3D de um pixel.

Modelagem de formas complexas e detalhadas, eficaz em contextos onde a volumetria é importante, como em simulações médicas e jogos de construção.

Voxel é sua simplicidade na manipulação e edição, permitindo operações como subdivisão e transformação de maneira intuitiva -> exige mais recursos computacionais

Aparência menos suave em comparação com malhas

![image](https://github.com/user-attachments/assets/10ceaa04-f075-473d-a88a-81aa5ca6b530)

### Curvas e superfícies paramétricas

Representações matemáticas descrevem formas complexas de maneira eficiente.

Os pontos são definidos por uma função que relaciona um ou mais parâmetros a coordenadas no espaço -> modelagem de objetos orgânicos e detalhados.

Criação de modelos complexos, como carros e personagens, onde detalhes finos são necessários.

Entendimento sólido de matemática.

Podem ser mais desafiadoras em termos de implementação e renderização

![image](https://github.com/user-attachments/assets/4ceefea3-6d51-4efc-bdba-39ac973645a9)

### Superfície implícita

Função matemática que determina se um ponto no espaço pertence à superfície ou não.

Formas complexas e suaves, como esferas e toróides, de maneira eficiente, sem a necessidade de uma malha explícita.

Capacidade de lidar com topologias complicadas.

Mais desafiadora em termos computacionais e pode requerer mais esforço para a visualização em tempo real.

## Modelos de câmera

### Esteroscópia

Garante imersão, pois apresenta uma visualização mais cara graças a quantidade de informações (analisar textura, minúcias).

![image](https://github.com/user-attachments/assets/011b9d21-a343-4047-8e42-d49a9cc10afb)

### Perspectiva

Versão mais barata.

Utiliza a ideia que os objetos mudam de tamanho conforme a distancia do objeto e centro da câmera, representação na tela, enxergando nossa realidade

Não considera duas imagems (apernas uma).

Oportunidade de perceber o espaço.

Ex: GTA

![image](https://github.com/user-attachments/assets/2039b6d6-aa93-42e1-a482-5ea82f0147c7)

### Ortografica

Mais barata das três, apresenta a analise bidimensional do ambiente, tudo fica em 2D para olhar com atenção em todos os objetos, de maneira que todos os elementos têm o mesmo peso visual.

Tudo fica equilibrado sem perspectiva.

Usado principalmente em jogo 2D, onde o player enxerga o objeto todo de uma vez sem distorções.

Ex: Starder Valley

![image](https://github.com/user-attachments/assets/c783b90d-268f-40b5-9766-edcc48a67920)


## Iluminação local e global

### Iluminação local

Depende apenas da superfície refletida e da fonte de luz.

Sombras básicas e sem reflexões entre ambientes o objetos.

![image](https://github.com/user-attachments/assets/ac615290-eccc-4823-b19b-21e1eebf3473)

Menos custoso e não gera muita interferência de luzes, por outro lado, causa a falta de realismo.

Modelos comuns: Phong e Blinn-Phong.

### Iluminação global

Cálculo e simulação de como a luz interage com todos os objetos em um ambiente virtual, levando em consideração todas as suas interações e reflexões.

Simula iluminação indireta.

![image](https://github.com/user-attachments/assets/1e5ad94f-b729-4978-975d-0a0872a8eef7)

![image](https://github.com/user-attachments/assets/b713a71a-0099-48fb-a41d-4e73ee85a633)

Possíveis interações:  

- Reflexões,
- Refrações e
- Oclusão ambiental.

Comportamentos:
- Reflexão Difusa: luz espalhada em todas as direções, dando cor aos objetos.
- Reflexão Especular: luz refletida em um único ângulo, criando brilhos.
- Refração: mudança de direção da luz ao passar por diferentes meios.
- Oclusão Ambiental: ausência de luz em áreas inacessíveis.

Algoritmos usados:

- Ray Tracing: simula o caminho da luz através do ambiente.
- Radiosidade: calcula a troca de energia radiante entre as superfícies.
- Photon Mapping: combina elementos de Ray Tracing e Radiosidade.

![image](https://github.com/user-attachments/assets/c1321b53-1b39-422c-b943-181c4eb48b38)

Modelos avançados: Ray Tracing, Path Tracing.

## Modelo de iluminação Phong

Técnica usada em computação gráfica para simular como a luz interage com superfícies, adicionando realismo a objetos 3D.

Calcula a iluminação de forma local, ou seja, diretamente sobre cada ponto da superfície sem considerar a luz refletida de outros objetos.

É amplamente usada por equilibrar simplicidade e eficiência com um nível de realismo visual adequado para diversas aplicações.

### Funções da Iluminação:

- Profundidade e Forma: a iluminação ajuda a definir a forma dos objetos, permitindo distinguir detalhes de textura e contornos.

- Efeito de Materialidade: diferentes tipos de iluminação simulam materiais distintos, dando a cada um propriedades únicas como brilho, rugosidade ou suavidade.

- Imersão e Realismo: aprimora a experiência visual através de uma boa iluminação aumenta a sensação de realismo e a imersão do usuário.

### Componentes:

- Ambiente: representa a luz ambiente que ilumina o objeto de forma uniforme, simulando a luz que é refletida de outras superfícies - **luz espalhada no ambiente**.

- Difusa: simula a dispersão da luz em superfícies não brilhantes, como madeira ou pedra, sendo dependente do ângulo entre a luz e a superfície - **brilho que atinge diretamente a superfície**.

- Especular: representa o brilho e é visível em superfícies polidas, como metal ou vidro, dependendo do ângulo entre o observador e a luz - **brilho mais intenso, simulando reflexos em materiais brilhantes**.

![image](https://github.com/user-attachments/assets/71dd718d-97a5-4b22-bdce-8f02a1fd18b3)

### Cálculo

Iluminação Total Phong = Ambiente + Difusa + Especular

Cada um desses componentes é calculada separadamente e depois somada para obter o resultado final.

Isso permite flexibilidade no controle de cada tipo de iluminação, ajustando a intensidade e cor de cada componente.

![image](https://github.com/user-attachments/assets/f0ee1146-774e-4a4e-b783-6d29efb59132)

### Diferenças entre o modelo Phong e outros

Modelo Lambertiano:

- Calcula apenas a luz difusa sem brilho especular, resultando em superfícies foscas.

- Não simula reflexos como o Phong, sendo menos realista e é mais leve computacionalmente.

Modelo Blinn-Phong:

- Usa fórmula para brilho mais eficiente e menos sensível ao ângulo de visão.

- É mais rápido para reflexos especulares e gera um resultado visual similar comparado ao Phong.

Modelo Cook-Torrance:

- Baseado em física realista, simula materiais complexos como metais e vidros.

- Difere do Phong por produzir reflexos precisos e texturas realistas, ideal para renderizações de alta qualidade com maior custo computacional.

![image](https://github.com/user-attachments/assets/931f5464-b2d0-4f72-8ced-ee8d9fb0142a)

![image](https://github.com/user-attachments/assets/bbda445a-e3f7-417d-8992-e2ec3d23c2cd)

![image](https://github.com/user-attachments/assets/3ab151bc-5bc5-4742-b62a-cad9f23ba35c)

Usado até hoje pois consigo fazer alguns calculos simples em aplicações de tempo real (Ex: jogos) e ter uma visualização muito interessante.

## Tonalização ou Shading

### Tonalização

Aplicar cores e tons a uma imagem/objeto e criar um efeito visual específico.

Cria profundidade, textura e realismo.

Pontos principais: cor bases, tons e matrizes e realismo.

### Shading

Adicionar sombras e simular efeitos de luz.

Textura e reflexos.

Tipos de shading:
- Flat shading
- Gouraud shading
- Phong shading

### Flat shading

- Aplicação de uma única cor
- Sem suavização
- Resulta em um visual mais "quadrado"/facetado
- Jogos retrô/vintage
- Visualizações de engenharia

### Gouraud shading

- Suaviza as transições de cor
- Cria um efeito mais leve e natural
- Mais eficiente que as outras técnicas, pois iluminação é calculada somente nos vértices
- Boa para superfícies sem reflexos intensos
- Simulação em tempo real (suavidade suficiente sem sobrecarregar o sistema)

![image](https://github.com/user-attachments/assets/bc4e97a5-c3da-4928-ab0d-4729b0fc49fe)

### Phong shading

- Nível mais alto de suavização
- Calcula a iluminação de forma mais precisa
- Cálculo é feito em cada pixel
- Superfícies extremamente suaves e realistas
- Design de produtos, renderização de alta qualidade

![image](https://github.com/user-attachments/assets/9bfe629a-b167-4d66-b3f1-d245333704ef)

![image](https://github.com/user-attachments/assets/029beb1f-a55f-4e69-885b-44596a29b6db)

### Limitações

Flat:

- Facetada e sem suavização.
- Não captura variações sutis de luz e sombra.

Gouraud:

- Pequenos reflexos podem ser perdidos por conta do cálculo no vértice.
- Não pega brilhos pontuais.
- Pode não capturar nuances em animações.

Phong:

- Custo computacional elevado.
- Complexidade de implementação.

## Mapeamento de texturas

No processo de mapeamento UV, o modelo 3D é "desdobrado" em uma superfície 2D, criando um "layout UV".

Esse layout distribui a geometria do objeto como um mapa plano que recebe a textura.

Aqui estão as etapas principais:

Desdobramento:

- Primeiro, define onde "cortar" o modelo, dividindo a geometria em seções planas que possam ser abertas sem distorção excessiva.

Layout UV:

- Organiza o layout no editor UV, ajustando a posição de cada face para ocupar o máximo de espaço da textura, garantindo uma resolução adequada.

Costuras e Alinhamento:

- Cuida das costuras para minimizar linhas visíveis e ajusta o alinhamento para manter as partes contínuas da textura, evitando quebras visíveis entre diferentes partes do modelo.

Ajustes Finais e Testes:

- Refina o layout, verificando a aplicação da textura para assegurar que não há distorções.

### Coordenadas UV

As coordenadas UV vão de (0,0) a (1,1), onde:

- (0,0) representa o canto inferior esquerdo.
- (1,1) representa o canto superior direito da textura.

Essas coordenadas determinam quais partes da textura ficam em quais áreas da superfície do modelo 3D.

![image](https://github.com/user-attachments/assets/094c7162-8224-4a67-98f1-7a411a180325)

![image](https://github.com/user-attachments/assets/02ee9f60-a142-4055-b4d3-763493077507)

### Tipos

- Mapeamento Automático: o software automaticamente gera um mapa UV, geralmente com cortes e junções automáticas.

- Mapeamento Manual: o artista ajusta e cria manualmente as coordenadas UV, definindo os cortes e o layout da textura.

- Mapeamento Esférico, Cúbico, Cilíndrico e Planar: esses tipos de projeções são úteis para objetos com formas específicas, onde a projeção de textura pode ser mais simples e eficaz.

![image](https://github.com/user-attachments/assets/6cde783b-841a-4f8e-9a0e-4d582344e028)

![image](https://github.com/user-attachments/assets/b47558a5-33d7-4394-b8cc-e7cfdbc09b78)

### Ferramentas

Blender: Oferece um sistema de UV muito robusto e inclui um editor UV.

Maya e 3ds Max: São populares para produções de alto nível, com ferramentas detalhadas de mapeamento.

Substance Painter: Usado para pintar texturas diretamente no modelo 3D, facilitando a aplicação de texturas complexas com base nas coordenadas UV.

# Aula 10

Especificações do Projeto 2.2