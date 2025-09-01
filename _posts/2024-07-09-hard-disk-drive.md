---
title: "Hard Disk Drive"
excerpt: "História, evolução, funcionamento, componentes, divisões, gravação e leitura dos HDDs."
categories:
  - Informática
tags:
  - HDD
  - Hard Disk
  - Informática
  - Disco
  - Cabeça de Leitura/Escrita
  - Trilhas
  - Setores
  - Cilíndros
  - Domínios
  - Preamble / Synchronization Zone
  - ECC
  - GMR
  - Horizontal/Vertical
  - PMR
  - SMR
  - HAMR

toc: true
---

## Introdução

Os discos rígidos (HDDs) são dispositivos essenciais para o armazenamento de dados, utilizando discos magneticamente revestidos para gravar e acessar informações digitais.

## História

O primeiro HDD comercial foi o IBM 305 RAMAC, lançado em 1956 pela IBM. Este dispositivo revolucionário tinha uma capacidade de armazenamento de 5 milhões de caracteres (cerca de 3,75 MB) distribuídos em cinquenta discos de 24 polegadas, girando a 1200 RPM.

## Evolução

Desde o IBM 305 RAMAC, os HDDs evoluíram significativamente. As capacidades de armazenamento aumentaram exponencialmente, e as velocidades de rotação dos discos melhoraram drasticamente, alcançando até 15.000 RPM nos modelos modernos.

### Componentes de um Hard Disk

![Untitled](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/9e63e4c7-a280-4475-9c68-ffcfdbf23ea6)

- **Prato (Disco):**
    - **Material:** Feito de alumínio ou vidro, revestido com uma camada magnética de cobalto.
    - **Função:** Armazena dados magneticamente.
- **Cabeçote de Leitura/Gravação:**
    - **Material:** Ligas metálicas e cerâmicas de alta precisão.
    - **Função:** Lê e escreve dados no prato utilizando princípios eletromagnéticos.
- **Atuador:**
    - **Material:** Geralmente um motor linear com componentes de aço e cobre.
    - **Função:** Move os cabeçotes de leitura/gravação para a posição correta sobre o prato.
- **Motor do Eixo:**
    - **Material:** Componentes de aço e ímãs.
    - **Função:** Gira os pratos a uma velocidade constante.
- **Placa Controladora:**
    - **Material:** Circuitos integrados de silício.
    - **Função:** Gerencia as operações do disco, incluindo a comunicação com o computador e o controle das funções do HDD.

## Funcionamento dos Hard Disks

Os HDDs armazenam dados em trilhas circulares nos pratos, divididas em setores, que são as menores unidades de armazenamento. Durante a gravação, o cabeçote de gravação altera o estado magnético dos domínios no prato para representar bits de dados. Durante a leitura, o cabeçote detecta essas mudanças magnéticas e as converte de volta em dados digitais.

## Divisões no Disco

![Untitled 1](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/e5075626-a30a-4afa-b341-606489591fdf)

![Untitled 2](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/61302b5b-f0e0-4628-810b-cb8ee68853b0)

- **Trilhas:** Círculos concêntricos no prato.
- **Setores:** Divisões dentro das trilhas, geralmente de 512 bytes ou 4096 bytes cada e é uma unidade física de armazenamento.
- **Cilindros:** Conjunto de trilhas alinhadas verticalmente em todos os pratos.
- **Domínios Magnéticos:** Pequenas áreas no prato magnetizadas em diferentes direções para representar bits de dados.

### Subdivisões do Setor:

- **Preamble / Synchronization Zone (Pré-ambulo / Zona de Sincronização):**
    - **Função:** Estabelece um ponto de referência para o cabeçote de leitura/gravação, permitindo a sincronização adequada antes do início da leitura ou escrita dos dados.
- **Address (Endereço):**
    - **Função:** Contém informações de localização que identificam a posição exata do setor no disco, permitindo que o controlador do HDD encontre e acesse os dados rapidamente.
- **Data (Dados):**
    - **Função:** Área onde os dados reais são armazenados. Cada setor tradicionalmente armazena 512 bytes de dados, embora os HDDs modernos frequentemente usem setores maiores, como 4 KB (4096 bytes).
- **Error Correcting Code (ECC) (Código de Correção de Erros):**
    - **Função:** Armazena informações adicionais usadas para detectar e corrigir erros que podem ocorrer durante a leitura ou escrita dos dados, garantindo a integridade e a confiabilidade dos dados armazenados.

## Funcionamento da Leitura e Gravação

![Untitled 3](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/8983f82d-4401-4ad1-a598-cf32d49e3c1a)

![Untitled 4](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/a3376161-8ad7-4da1-912e-a5868ef5282f)

![Untitled 5](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/09efddce-53ff-424a-8386-5937815de609)

GMR

![Untitled 6](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/e19b3779-2ea4-4de2-b038-5536d325fb65)

![Untitled 7](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/61d23bd7-7661-41ba-8cdd-710709c29786)

**Leitura de Dados:**

- **Cabeçote de Leitura:** Localizado na extremidade de um braço móvel (atuador), o cabeçote de leitura é uma pequena bobina de metal que flutua sobre a superfície do prato do disco. Ele é projetado para "voar" muito próximo à superfície do prato, a apenas alguns nanômetros de distância, sustentado por um fino colchão de ar gerado pelo movimento rápido dos pratos.
- **Princípio Magnético:** Quando o prato gira sob o cabeçote de leitura, as áreas magnéticas no prato geram pequenas correntes elétricas na bobina do cabeçote. Essas correntes são interpretadas como dados binários (0s e 1s) pelo controlador do disco.

**Gravação de Dados:**

- **Cabeçote de Gravação:** Semelhante ao cabeçote de leitura, o cabeçote de gravação utiliza um campo magnético para alterar o estado magnético dos domínios no prato. Ele aplica uma corrente elétrica à bobina para criar um campo magnético que altera a orientação dos domínios magnéticos na superfície do prato.
- **Processo de Magnetização:** Durante a gravação, o controlador do disco envia dados digitais ao cabeçote de gravação, que os converte em pulsos de corrente para criar um padrão magnético no prato. Esses padrões magnéticos representam os dados que serão armazenados.

Horizontal

![Untitled 8](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/5b5c966b-60e4-4ba0-bb34-01c22a14e8e9)

A gravação magnética horizontal em discos rígidos utiliza a orientação dos domínios magnéticos na superfície do disco para armazenar dados. Neste método, os bits são representados pela direção horizontal dos domínios magnéticos, alinhados paralelamente à superfície do prato. Durante a gravação, um cabeçote de gravação aplica um campo magnético que altera a orientação desses domínios, definindo se o bit será registrado como 0 ou 1. O único problema é a densidade de armazenamento, pois requer domínios magnéticos grandes o suficiente para evitar interferências entre bits adjacentes.

![Untitled 9](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/da820a13-ae5e-4a2a-986c-368859b09e11)

Vertical
Por outro lado, a gravação magnética vertical, também conhecida como gravação perpendicular, supera esses desafios ao armazenar dados perpendicularmente à superfície do disco. Neste método mais avançado, os bits são registrados como pilares magnetizados que se estendem verticalmente. Isso permite uma densidade de armazenamento muito maior, pois os bits podem ser mais compactos e próximos uns dos outros, reduzindo significativamente as interferências entre eles. Com a gravação perpendicular, os discos rígidos modernos alcançam capacidades substanciais de armazenamento e oferecem maior confiabilidade na preservação dos dados.

Quando maior o tamanho de armazenamento, mais discos o HD possui.
![Untitled 10](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/2f43a5bd-50f4-4552-a06d-ac8d40e72816)

## Melhorias de Desempenho e Armazenamento

- **Cache:** Memória temporária que armazena dados frequentemente acessados para acelerar leitura e escrita.
- **ZBR (Zone Bit Recording):** Ajusta a densidade de gravação de dados em diferentes zonas do prato para maximizar a capacidade.
- **NCQ (Native Command Queuing):** Melhora o desempenho ao reordenar comandos de leitura/escrita para acesso mais eficiente aos dados.

![Untitled 11](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/e310017c-66c2-4549-9587-127adc8fe008)

- **Placas de Vidro:** Mais resistentes a choques e podem suportar maior densidade de dados que as de alumínio.
- **PMR (Perpendicular Magnetic Recording):** Armazena mais dados no mesmo espaço, orientando domínios magnéticos perpendicularmente ao prato.
- **SMR (Shingled Magnetic Recording):** Aumenta a densidade de gravação sobrepondo parcialmente as trilhas de dados.

![Untitled 12](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/365cc8b2-7de6-460d-bb03-b91350cb5ad8)

- **HAMR (Heat-Assisted Magnetic Recording):** Utiliza calor para gravar dados em domínios magnéticos menores, aumentando a densidade de armazenamento.

![Untitled 13](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/2c7dc092-b08d-424b-b4ed-fa77304742f5)