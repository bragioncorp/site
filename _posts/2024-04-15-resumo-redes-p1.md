---
title: "Redes de Computadores - Resumão para P1"
excerpt: "Resumo extenso que fiz através de perguntas e respostas para praticar."
categories:
  - Redes
tags:
  - Redes
  - Redes de Computadores
  - Resumão
  - Teoria
  - P1

toc: true
---

# Resumo para P1 de Redes de Computadores.

## Aula 1:
### Explique Canais broadcast x Ponto a Ponto + Locais x Esparsas + Públicas x Privadas.

Broadcast (difusão):  
    sinal difundido aos participante e cada um aceitará o pacote endereçado a ele.  
    usados em redes locais.  
    permite multicast (difusão para grupo).  
    topologias: barramento e anel.  

Ponto a ponto:  
    ligam pares de computadores (ligado a um ou mais).  
    vários nós podem formar uma malha.  
    usados em conexão de redes esparsas.  
    permitem unicast (um destino por vez).  
    topologias: irregular, estrela e completo.  

Redes públicas:  
    forma de comunicação por empresas de telefonia.  
    encaminham dados para tronco comum (ponto a ponto).  

Redes privadas:  
    redes de propriedade de um único dono, propriedade privada.  
    redefinem os limites para redes locais.  

### O que é PDU? Discuta seu header+payload e encapsulamento.

PDU:  
descreve o formato das mensagens trocadas entre camadas parceiras.  
possui header com informações de controle e um payload com PDU da camada superior.  

encapsulamento:  
a camada adiciona informação de controle em seu PDU, coloca o PDU da camada superior e envia à camada de baixo.  
o processo é invertido no destino.  

### Defina arquitetura de rede e pilhas.

Arquitetura de rede:  
conjunto de camadas e protocolos com informações detalhadas para a implementação do hardware ou software daquele nível.  

Pilha de protocolos:  
instância ou implementação de conjunto de protocolos usados em determinado sistema ou plataforma.  

### Apresente o Modelo OSI.

apresenta 7 camadas e é adotado como referência para estudo e projeto de redes.  
camadas:  
    1 - Física: representa os bits no meio físico (cabos).  
    2 - Enlace: controle de erros, fluxo e formas de enquadramento.  
    3 - Rede: controla operações sub-rede, roteamento e formas de endereço.  
    4 - Transporte: relação entre duas aplicações, divisão de dados e acesso à rede.  
    5 - Sessão: controle de diálogo, tokens e sincronização.  
    6 - Apresentação: sintaxe, semântica e encriptação das mensagens.  
    7 - Aplicação: protocolos ou serviços para a arquitetura de redes.  

### Defina a arquitetura internet.
criado pela ARPANET.  
evolução da arquitetura TCP/IP.  

1 - Host/rede:  
    não é descrita pelo modelo TCP/IP.  
    pode ser associada a qualquer tech de rede.  

2 - Inter-redes:  
    define funções parecidas com o modelo OSI.  
    o IP permite rotamente entre tecnologias distintas através de datagrama.  

3 - Transporte:  
    meio de comunicação "fim a fim".  
    dois protocolos: UPD (sem conexão e não confiável) e TCP (conexão confiável).  

4 - Aplicação:  
    protocolos para serviços oferecidos através da internet (http, telnet, ...).  
    função de sessão e apresentação.  
		
### Explique a diferença dos serviços com conexão ou não, confiável ou não.

Conexão  
definem interface baseada em fluxos.  
todos os bits são transmitidos ordenadamente da origem ao destino através de um "duto".  
ex: sistema telefônico.  

Sem conexão:  
transmissão de pacotes (dados) de forma individual e independente.  
podem seguir caminhos distintos e chegar fora de ordem.  
ex: correio.  

Confiável  
cada msg trocada entre origem e destino é confirmada.  
origem pode retransmitir msgs não confirmadas.  

Não confiável:  
a confirmação não é realizada pela camada em questão.  
msgs podem ser descartadas.  

## Aula 2
### O que são sinais? Defina sinal analógico e digital.

sinais são expressões de energia no tempo com uma certa frequência.  
tipos: elética, rf, luz.  
classificação:  
analógicos: variação contínua em relação ao tempo.  
digitais: variação discreta em relação ao tempo.  

### Explique as medidas: bandwitdh, atraso e throughtput.
Bandwitdh:  
mudanças de um sinal por segundo é conhecido como baud. ex: 9600 bauds.  
vários níveis discretos.  

teorema de nyquist:  
para uma taxa de reprodução de H (Hz), são necessárias 2H amostras.  
2H log(base 2)V  
3.8 kHz (4kHz) e 256 níveis discretos.  
ex: 2 x 4000 x log 2 256 = = 8000 x 8 = 64000 bps  

teorema de shannon  
efeito do ruído na transmissão como limitante da taxa de bits.  
H log(base 2)(1+S/N)  
S/N = 10^(N/10) e H = 3000  
ex: 3000 x log 2(1+1000) = 3000 x 9,9672= 29901 bps (menos que 30 kbps).  

Atraso:  
de propagação: tempo para o pacote percorrer o meio.  
de comutação: tempo para o componente encaminhar o pacote.  
de acesso: tempo para obter controle do meio.  
enfileiramento: tempo para enfileirar pacote na memória.  

Throughtput:  
mede a taxa de dados transmitidos através da rede.  
taxa efetiva de entrega de dados - sem erro.  

quando aumentar, o delay também pode aumentar.  
tráfego excessivo é conhecida como congestionamento.  

### Defina multiplexação: FDM, WDM e TDM.
divide o canal de comunicação em diversas linhas de transmissão.  

FDM:  
por divisão de frequência.  
faixa distinta de frequência.  
ex: TV e rádio  

WDM:  
por divisão em comprimentos de onda.  
aplicada à comunicações óticas.  

TDM:  
por divisão de tempo.  
comunicações puramente digitais.  
ex: redes locais.  

## Aula 3
### Explique o CSMA/CD.

acrescenta a detecção de colisão ao CSMA.  
a estação que vai transmitir deve ouvir o canal até que fique livre e então tranmitir.  
durante a transmissão, a estação monitora o canal para detectar uma possível colisão com outra estação.  
se uma colisão ocorrer, ambas param a transmissão e enviam um sinal avisando as outras sobre o ocorrido.  
as estações que colidiram devem esperar um tempo para tentar novamente.  
evitada em sistemas de tempo real.  

### Explique o CSMA/CA.

para uma estação transmitir ela deve ouvir o canal e enviar uma solicitação RTS (ready to send).  
o destino disponível deve responder com CTS (Clear to send).  
as demais estações ficam em silêncio por um tempo (NAV) esperando a transmissão e confirmação pelo destino (ACK).  
uma estação pode assumir o controle central usando quadro de beliza.  

### O qye é Switched ethernet? Como acontece o aprendizado em bridge?

equipamento para retransmissão seletiva de quadros que inibe a ocorrência de colisões.  

características importantes:  
a quantidade de memória (armazenar endereços da porta)  
velocidade do backplane (soma de todas as taxas de transmissão disponíveis).  

Aprendizado de bridge.  
as tabelas de IP e MAC são iniciadas vazias.  
para cada quadro que chega, a bridge analisa seu endereço de origem e associa ao MAC na tabela.  

## Aula 4
### Explique os tipos de serviços e header do IP.

número de 32 bits formam os endereços IP e são únicos na internet.  
a associação de números deve ser coordenada globalmente.  
principal protocolo de comunicação para enviar e receber dados na internet.  
permite que dispositivos se comuniquem, independente do hardware, sistema operacional ou arquitetura de rede.  

o header é composto de:  
Version					: versão do protocolo.  
IHL						: tamanho total do header do pacote.  
Total Length			: tamanho total do pacote em bytes (max 65535).  
Type of Service			: indica a qualidade do serviço de roteamento para transmissão dos dados.  
Identification			: valores que ajudarão na reconstrução do datagrama.  
Flags					: campo de 3 bits.  
Fragment Offset			: posição de início em bytes do fragmento dentro do datagrama.  
Time to Live			: tempo máximo de vida do datagrama.  
Protocol				: número do protocolo do próximo nível superior.  
Header Checksum			: soma binária para conferência do cabeçalho.  
Source Address			: endereço IP do remetente.  
Destination Address		: endereço IP do destinatário.  
Options					: campo opcional.  
Padding					: completa o options.  
	

### Explique endereço: prefixo/sufixo, classes (tamanho) da rede/broadcast.

prefixo: identifica a rede ou sub-rede.  
sufixo: identifica a interface naquela rede.  

classes:  
A: 0 - 127.  
B: 128 - 191.  
C: 192 - 223.  
D: 224 - 239.  
E: Reservada para o futuro.  

Máscara: rede e subrede.  
máscara de rede (netmask):  
classe A:  
    255			0			0			0  
    11111111	00000000	00000000	00000000  
    /8  
classe B:  
    255			255			0			0  
    11111111	11111111	00000000	00000000  
    /16  
classe C:  
    255			255			255			0  
    11111111	11111111	11111111	00000000  
    /24  

máscara de subrede  
255			255			255			128  
11111111	11111111	11111111	10000000  
/25  

255			255			255			224  
11111111	11111111	11111111	11100000  
/27  

### Tabela de rotas: criar e interpretar.

1 - redes conectadas diretamente: GW = 0.0.0.0  
2 - roda default: destino e máscara = 0.0.0.0  
3 - outras redes  
	Só da para estudar e praticar pelo desenho (em breve).  
	   
## Aula 5
### Descreva sobre o conceito de ICMP e seus principais usos.

fornece uma comunicação de controle para o protocolo IP.  
evita o encaminhamento de erros da camada de rede para a origem (inexistência de rotas, sem resposta ARP e expiração do TTL).  
é encapsulado em um datagrama IP.  

usos:  
teste de alcance:  
através do ping.  
usa ICMP ECHO.  
calcula o tempo até o pacote chegar em outro host.  

descoberta de rotas:  
através do traceroute.  
host A envia ICMP ECHO com TTL incremental para B.  
host B decrementa e devolve com "tempo excedido".  
host A calcula o tempo e repete isso até o destino final.  

descoberta do menor MTU do caminho:  
é importante para evitar fragmentação.  
host encaminha um pacote com MTU local e flag "don't fragment".  
ao chegar em outro host e detectar MTU menor, descarta o pacote e envia um ICMP "framengtation required" à origem.  
host origem repete com um pacote menor.  

### Descreva sobre o conceito de ARP e seu uso no encaminhamento local do IP.

padroniza o formato da mensagem para a resolução de endereços IP.  
tradução de endereços de rede para endereços de hardware.  

encaminhamento:  
o host monta uma mensagem ARP com o endereço IP de destino e preenche o endereço de hardware com 0.  
como não conhece o destino, usa endereço broadcast FF:FF:FF:FF:FF:FF.  
o destino pega o quadro e faz o mapeamento IPxHW da origem, armazena, troca os dados os dados emissor/destino e envia resposta unicast.  

### Quais são os tipos de encaminhamento?

direto:  
destino está conectado na mesma rede física que a origem.  
datagrama IP enviado diretamente.  
a origem cria um quadro com seu MAC e o MAC do destino.  

indireto:  
destino e origem em rede físicas diferentes.  
datagrama IP enviado para um gateway.  
a origem cria um quadro com seu MAC e o MAC do gateway (destino).  

### Comente a ideia geral da fragmentação.

usada pelo IP.  
o roteador deverá fragmentar o IP se receber um pacote onde o MTU anterior for maior q o próximo.  
cada framento consistirá de um novo datagrama IP, sendo o mesmo header.  
o fragment offset fornece a posição no datagrama original.  
um bit no header inidica se é o último ou não.  

a remontagem do datagrama origital ocorrerá no destino, pois os fragmentos podem passar por diferentes nós e chegar fora de ordem.  

### Descreva sobre o conceito de NAT e a aplicabilidade do IPv6

network address translator minimizou o problema da disponibilidade e de divisão do IPv4.  
permite o uso de endereçamento particular (intranet).  

o IPv6 é uma versão expandida q veio "substituir" o IPv4.  
não suporta NAT, pois cada dispositivo conectado recebe um IP real.  
não vai substituir, e sim coexistir com.  