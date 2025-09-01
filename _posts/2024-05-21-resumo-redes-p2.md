---
title: "Redes de Computadores - Resumão para P2"
excerpt: "Resumo filtrado que fiz através de perguntas e respostas para praticar."
categories:
  - Redes
tags:
  - Redes
  - Redes de Computadores
  - Resumão
  - Teoria
  - P2
  - Cliente-Servidor
  - UDP
  - Header UDP
  - TCP
  - Header TCP
  - Etapas da Conexão TCP
  - Janela Deslizante
  - Telnet
  - NVT
  - SSH
  - FTP
  - DNS
  - SMTP
  - POP3
  - IMAP
  - Proxy
  - CUPS
  - SAMBA
  - DoS
  - DDoS
  - SYN Attack
  - Trojan
  - Sniffer
  - Scanner
  - Probe
  - Criptografia
  - Chave Simétrica
  - Chave Assimétrica
  - Hash

toc: true
---

# Resumo para P2 de Redes de Computadores.

## AULA VII
### O que é UDP? Explique seu header.
É um serviço de datagrama semelhante ao IP.  
Não é orientado à conexão e nem confiável.  
Não reordena as mensagens antes de entregar à aplicação e nem garante a chegada de todas as mensagens.  
	
o UDP é muito simples e define apenas:  
- 32 bits totais.
- Endereços das portas de origem e de destino.
- Tamanho atual (UDP length) em bytes do datagrama (header + data).
- Checksum (opcional)

> A maior vantagem do UDP é ser um protocolo simples com poucos campos no header (pouco overhead).

### O que é TCP? Explique seu header.
É o principal protocolo de transporte da internet.  
Oferece um serviço baseado em stream (fluxo), orientado à conexão e confiável.  
Realiza a transmissão ordenada e confiável através de uma conexão preestabelecida.  
Essa conexão é mantida durante o serviço e encerrada no final.  
	
O header do TCP é muito mais completo:  
- 32 bits.
- Portas de origem e destino.
- Sequence number, acknowledgment number.
- TCP header length, URG, ACK, PSH, RST, SYN, FIN, Windows Size.
- Checksum, Urgent Pointer.
- Options.
- Data (opcional).

### Explique os campos do header TCP.
Sequence number: número de sequência (por conexão) do TPDU.   
Acknowledgement number: descreve o número de sequência do TPDU que está sendo confirmado.  
TCP header length: tamanho do cabeçalho TCP em palavras de 32 bits.  

Flags:  
URG: se 1, indica que o campo Urgent pointer foi usado e que existem dados urgentes (interrupção).  
Urgent pointer indica através de um byte offset qual número de sequência (em relação ao TPDU atual) trará os dados urgentes.  
ACK: se 1, indica que o campo Acknowledgement foi usado.  
PSH: comunica à entidade de transporte no destino para entregar cada mensagem que chega e não esperar para entregar todas de uma vez.  
RST: é utilizado para solicitar o reset (restabelecimento) de uma conexão que apresenta problemas.  
SYN: é usado para solicitar/aceitar o estabelecimento de uma conexão.  
FIN: é usado para solicitar/aceitar o encerramento de uma conexão.  
Window size: indica o tamanho da janela a ser utilizada no controle de fluxo através do algoritmo de janela deslizante.  

### Dê exemplos de aplicabilidades do TCP e do UDP e explique.
#### Aplicações TCP:
É o protocolo a se escolher para confiabilidade e qualidade máximas. Pode não ser o mais rápido, mas entrega os dados sem erro.  
	
- envio de e-mails e de mensagens de texto.
- transmissão de conteúdos pré-gravados em sites como Netflix, Hulu ou HBO Max (media stream).
- transferência de arquivos entre aplicativos e dispositivos.
- navegação na web em geral.
- administração remota de dispositivos ou redes.
	
#### Aplicações UDP:
O UDP é mais adequado para transferir um fluxo constante de dados ao vivo, permitindo que os usuários tenham acesso aos dados de forma fácil e rápida. Pode devolver ótimas ou péssimas qualidade devido a perda de dados.  

- jogos online.
- multitransmissão.
- chamadas de vídeo/videoconferência.
- live broadcasting.
- voIP (chamada de voz por aplicativo).
- sistemas de nomes de domínio (que traduzem nomes de domínio em endereços de IP).

### O que é paradigma cliente-servidor?
Aplicações em rede relacionam-se em pares: cliente e servidor.  

O servidor (papel passivo) aguarda a solicitação de conexões e serviços de outras aplicações.  
O cliente (papel ativo) solicita conexões e serviços.  

### Defina o comportamento cliente-servidor. Quais as principais interações?
#### Sevidor
Aguarda a mensagem com requisição (pode conter dados).  
Executa o serviço solicitado.  
Envia a mensagem de resposta (pode conter dados).  

#### Cliente
Envia mensagem de requisição ao servidor.  
Aguarda o retorno da mensagem com a resposta.  

#### Interações
Cliente pode acessar vários servidores diferentes.  
Cliente pode acessar vários servidores de um mesmo serviço.  
Servidores podem se tornar clientes de outros servidores.  
Host pode executar várias aplicações clientes e/ou servidores.  

### O que é comum tanto no TCP quanto no UDP?
#### Porta  
Identificador único local (número de 16 bits) que descreve e registra as aplicações em execução, atendidas pela pilha TCP/IP.  

#### Multiplexação
Várias aplicações clientes/servidores podem compartilhar os serviços de uma  mesma entidade de transporte.  
	
Servidor usa a porta para se registrar localmente.  
O cliente pode informar a porta à camada de transporte.  

### Explique o processo de conexão TCP.
Técnica three-way handshake.  

- O servidor aguarda uma conexão em estado de LISTENING e deve ter executado uma chamada bloqueante de um ACCEPT.
- O cliente pode solicitar uma conexão (CONNECT), que enviará um TCP com os flags SYN=1 e ACK=0
- O servidor checará se a porta escolhida esta aceitando conexões, caso contrário envia uma resposta com o flag RST=1, rejeitando a conexão.
- Caso dê certo, ele aceita a conexão, através de uma confirmação (acknowledgment), com os flags SYN=1 e ACK=1.
- O processo de encerramento de uma conexão é semelhante.

### Explique o processo de confirmação TCP.
O destino envia uma mensagem de controle com Confirmação (Acknowledgment - ACK) para a origem verificar a entrega da mensagem com sucesso.  
A origem inicializa o relógio, se o tempo expira antes da confirmação, ele inicia o relógio e retransmite.  

### Explique o tempo de expiração TCP.
É o tempo dado para entregar o pacote até sua perda e deve ser diferente para cada conexão e inicializado dinamicamente.  
O tempo de entrega na Internet muda dinamicamente e o tempo de expiração deve se adequar.  
	
O tempo expiração é baseado em RTT (Round Trip Time).  
- Emissor não pode prever o RTT antes de uma transmissão.  
- Então define o RTO (Retransmission Timeout) baseado em um prévio RTT.  

### Comente sobre o gerenciamento de janela.
O TCP usa janela deslizante para controle de fluxo e descreve quais bytes do stream podem ser enviados.  
O Destino especifica o tamanho da janela (window advertisement) e envia uma confirmação para o próximo byte que pode ser enviado e o número de bytes que pode aceitar no fluxo atual, transportado como ACK.  

### Controle de congestionamento.
É um controle para avisar sobre o congestionamento de dados na rede através de uma janela de congestionamento.  

Inicialmente a janela tem um tamanho mínimo para indicar o volume total de mensagens que podem ser encaminhadas à rede antes de receber uma confirmação (mensagens pendentes). A janela aumenta gradativamente à medida que o RTT médio das confirmações diminui e vice-versa.  

Quando detectado um congestionamento (por timeout da confirmação), a janela é reduzida drasticamente, mas pode voltar a crescer com o passar do tempo.  

## Aula VIII
### Compare Telnet com SSH.
#### Telnet
Serviço de emulação de terminal virtual, sobre uma conexão TCP, através da porta 23.  

Através de um NVT (Network Virtual Terminal), permite que o usuário realize uma sessão de terminal virtual, e a emulação se comunica com um processo servidor (telnetd) através da Internet.  

Cada caractere digitado pelo usuário é encaminhado ao servidor e ecoado de volta para ser exibido na tela.  
	
#### Problema do Telnet
A segurança, pois os dados trocados durante a sessão de um terminal são transmitidos em texto plano (sem encriptação).  
Os dados são facilmente comprometidos pelos sniffers.  
	
#### SSH
Secure shell.  
Implementação segura da emulação de terminal virtual através da porta 22.  

Apresenta mecanismos para autenticação segura de usuários, confirmação de integridade de mensagens e encriptação de conteúdo (RSA de chaves assiméticas, DES, 3DES, AES).  

Pode dar suporte à comunicação segura de outros tipos de aplicações através de um canal (túnel) seguro.  

### Explique FTP. Quais são seus modos?
File transfer protocol.  
Protocolo padrão de transferência de arquivo.  
Define um mecanismo para transferência de arquivos com conteúdo ASCII ou binário, através do estabelecimento de duas conexões TCP:  
> Porta 21 opera o canal de controle.  
> Porta 20 opera o canal de dados.  
	
#### Modos
- Ativo:  
    Cliente se conecta à porta 21 do servidor e informa o número da outra porta que será utilizada para receber a conexão de dados.  
    Costuma apresentar problemas em operações através de firewalls.  

- Passivo:  
    Cliente realiza uma conexão à porta 21 do servidor e informa que o modo será passivo.  
    Abre uma conexão com a porta 20 do servidor para o canal de dados.  

### Explique DNS. O que é FQDN?
Domain Name System.  
Usa a porta 53.  

Os endereços IPs são eficientes à comunicação TCP/IP, porém inadequados à memorização humana e não faz referência geográfica.  
O DNS provê a tradução dos IPs para nomes.  
	
FQDN:  
Fully-Qualified Domain Name.  São os nomes completos compostos por sequências de alfanuméricos separados pontos:  
- parte mais à esquerda: nome do host.  
- parte da direita: domínio (e sua hierarquia).  

### Comente a hierarquia DNS.
A hierarquia do DNS define domínios de alto nível (TLDs - Top level domains) através de uma autoridade global (InterNIC), classificados como:  
	
	Por atividade:
		.com
		.edu
		.gov
	
	Geográficos:
		.br
		.fr
		.ca

### Explique o processo de resolução DNS.
Se a solicitação contém um nome gerenciado pelo servidor receptor, este responde diretamente.  

Caso contrário, a solicitação deve ser encaminhada ao servidor autoritativo apropriado, através de uma busca iterativa.  
Um DNS pode atuar como resolver (cliente) para evitar que todas as requisições sejam feitas diretamente à autoridade.  

O servidor DNS se torna cliente do servidor autoritativo (e da hierarquia) ao realizar a solicitação pela resolução de nomes no lugar do cliente origem.  

### Explique um resolver (interação c/ cliente).
DNS resolver é associado ao servidor local, que fará o cache da resolução, pesquisando na hierarquia de zonas de autoridade.  

### O que é HTTP? Quais seus métodos?
Protocolo definido para a comunicação entre aplicações Web.  

#### Alguns campos do header HTTP
Content-Encoding - tipo de compressão do conteúdo.  
Content-Language - código da linguagem natural do conteúdo.  
Content-Length - tamanho em bytes do conteúdo.  
Date - data e horário de criação da mensagem.  
Content-Type - o tipo de conteúdo (MIME - RFC 822) transportado pela mensagem.  

#### Métodos
GET - solicita que o servidor envie a página referenciada pela URL (pode conter parâmetros extra).  
PUT - solicita que o servidor receba um documento, em um formato MIME (informado no Content-Type) e armazene na URL informada.  
POST - solicita que o servidor receba dados (no conteúdo) para serem informados a um documento (normalmente um programa) especificado pela URL.  

### Explique a interação HTTP:
Baseia-se em “hits” de requisição/resposta.  

#### Request  
Enviada pelo cliente com conteúdo ASCII e as linhas de texto são separadas por blank lines.  

#### Response  
Enviada pelo servidor com conteúdo MIME especificado no campo Content-Type.  

Cada requisição HTTP realizada pelo cliente representa a solicitação de um recurso hipermídia.  
Ou seja, gera uma nova conexão TCP para cada recurso e é encerrada na resposta.  

### O que é URL?
É o endereço na web para acessar alguma página. Especifica o protocolo, usuário, senha, host, porta, detalhes do caminho e algum parâmetro (caso necessário).  
	
    Ex: https://www.google.com.br/search?hl=pt-BR&q=teste&btnG=Pesquisa+Google&meta=  

### O que é Proxy?
Atua normalmente como um cache para rede local.  

Passos:
- Clientes solicitam todos os objetos hipermídia ao servidor proxy.
- O servidor proxy intermedia a comunicação com o servidor web e obtém o recurso solicitado.
- Armazena uma cópia do mesmo e associa a sua identificação (URL) e o seu timestamp.
- O recurso então é enviado ao cliente que solicitou.
- Quando ocorrer a próxima solicitação do mesmo recurso, o servidor proxy pode decidir por encaminhar a cópia que mantém em cache, evitando um novo contato com o servidor web.

## Aula IX
### O que é SMTP?
Simple Mail Transfer Protocol.  
O funcionamento básico consiste em enviar mensagens para caixas postais (mail boxes):  

- Um cliente (user agent) pode acessar as caixas postais locais.  
- Um cliente pode também efetuar encaminhamento das mensagens através do servidor (MTA – Message Transfer Agent).  
- As mensagens recebidas de outros MTAs são armazenadas nas caixas postais dos usuários.  
	
A identificação de uma caixa postal inclui o nome do usuário (login name) e o nome do host onde se localiza.  
> formato: login_name@host_name 

### O que é MIME?
Extensão ao SMTP que permite a inclusão de outros conteúdos além de texto puro ASCII.  

Base para interpretação de conteúdos convertidos em ASCII por outras aplicações, como o HTTP.  
Um usuário pode anexar partes distintas a uma mensagem (arquivo executável, figura) e o cliente (user agent) informará o tipo MIME do conteúdo.  

O conteúdo é codificado como conteúdo ASCII puro e inserido no corpo da mensagem, devidamente delimitado e identificado.  

### O que é POP3?
Post Office Protocol.  
Usa a porta 110.  

A caixa postal de um usuário pode ser armazenada em uma máquina diferente de onde é executado o cliente (user agent).  
Permite a listagem, o download e a remoção de mensagens de uma caixa postal remota.  

Originalmente definido para a solução do problema de acesso a caixas postais remotas usando o serviço dial-up (dado o problema com o custo de se manter o acesso contínuo).  

> Implementação bem conhecida do POP3 server: Qpopper.  

### O que é SAMBA e CUPS? Quais suas funcionalidades?
#### SAMBA
Conjunto de ferramentas de código aberto que provê serviços de acesso a arquivos e impressoras em rede, para clientes SMB (Server Message Block).  
Usa a porta 445.  
	
#### CUPS
Commmom Unix Printing System.  
Usa a porta 631.  
Interface web para administração de impressoras e filas de impressão.  
Proporciona um meio de impressão portátil e padronizado para os sistemas baseados em Unix.  
	
#### Funcionalidades
- SAMBA:  
    Serviços de arquivos e Impressão.  
	Autenticação e autorização.  
	Resolução de nomes.  
	Browsing (anúncio de serviços).  

- CUPS:  
	Permite a instalação de impressoras PDF, filtragem extensível de arquivos e interfaces backend de dispositivos.  
	Serviços de diretório de impressoras em rede e função de encriptação.  

## Aula X
### Liste os requisitos e ameaças.
#### Requisitos
- Disponibilidade  
    O sistema deve funcionar adequadamente fornecendo recursos aos usuários autorizados sem degradação de acesso.  

- Integridade  
    A informação deve permanecer intacta e inalterada por acidentes e ataques.  

- Confidência  
	A informação deve ser acessada somente por pessoas autorizadas para tal.  
	
#### Ameaças
- Interceptação  
    Acesso não autorizado à informação ou sua cópia ilegal.  
    Ameaça ao requisito de CONFIDÊNCIA.  

- Interrupção  
	Quando a informação torna-se inacessível.  
	Indisponibilidade de um serviço ou destruição dos dados.  
	Compromete o requisito de DISPONIBILIDADE.  

- Modificação  
    Alteração não autorizada/especificada dos dados ou em serviços.  
    Em redes geralmente precedida pela interceptação.  
    Fere o requisito de INTEGRIDADE.  

- Fabricação/falsificação  
    Criação de dados ou de eventos que não deveriam existir.  

### Discuta os principais ataques.
#### Sniffer  
Monitor promíscuo que intercepta o tráfego de pacotes.  
Atua em redes de difusão (broadcasting).  

Os conteúdos sem encriptação são obtidos facilmente pelo atacante principalmente para a obtenção de senhas.  

#### Scanner
Submete pesquisas a um host (ou vários).  
Objetivo de obter informações sobre o sistema como portas servidoras (aplicações) que estão operantes.  

- Comportamento comum:  
    Realiza conexões ou envia pacotes de reconhecimento para as portas do sistema.  

- Geralmente precede um probe (tentativa de acesso).  
    Consiste normalmente do primeiro passo de um ataque (reconhecimento de área).  
	
#### Probe
Tentativas sucessivas de acesso a aplicações.  
Comportamento comum:  

- Tentativas sucessivas de acesso às aplicações servidoras.  
- São usadas senhas óbvias ou vulnerabilidades conhecidas dos serviços em execução.  
- Obtenção de dados sobre versões das aplicações e do sistema operacional.  
Uso de ferramentas e kits (exploits) prontos.  
	
#### SYN Attack
Explora uma deficiência no protocolo TCP.  

Solicitam inúmeras requisições SYN consecutivas, porém não devolvem o ACK.  
O servidor fica saturado de conexões pendentes e pode deixar de atender clientes.  

#### O que é DoS? E DDoS?
- DoS:  
    Saturação da rede (“flood”) ou das conexões.  
    Normalmente são utilizados ataques SYN.  
    Interrompe serviços e comunicações.  
    Compromete o requisito de DISPONIBILIDADE.  
    Difícil de se rastrear (origens são falsificadas - IP spoofing).  

- DDoS:  
    Amplificação de um DoS.  
    Scan em um grande número de hosts.  
    Hosts e até redes inteiras ficam inacessíveis.  
    Comprometem um site, uma rede ou até grandes domínios.  
    Até centenas de daemons distribuídos originarão o ataque.  
    Invasão e instalação de ferramentas de ataque nos hosts.  
    Instalação de sniffers.  
    Envio dos dados coletados a um servidor central.  
	
#### Trojan / Malicious code
São códigos ou conjunto de códigos que exploram falhas no ambiente do usuário como antivírus desatualizado, aplicativos vulneráveis e envolvem os usuários do sistema.  

Apresentam consequências graves.  
Criação backdoors para o processo de propagação em grande escala (mutação) ou para futuro comprometimento do sistema.  
	
#### Explique a evolução dos códigos maliciosos.
#### Backdoors:  
Furos de aplicações ou instalados pelo usuário desavisado.  
Abrem portas servidoras, permitindo acesso de fora.  

#### Malwares:  
O uso de NAT escondeu as portas servidoras das máquinas da Intranet, o que motivou a evolução dos malwares para clientes.  

Os malwares clientes não podem mais acessar portas externas (firewall e proxy).  
Passaram a se comunicar por protocolos Web (HTTP) e propagam-se com a ajuda dos usuários e se valem dos acessos que eles têm.  

### O que é firewall?
Equipamento (ou sistema) que permite o controle de segurança na comunicação entre duas ou mais redes.  
Geralmente atua como um filtro, permitindo pacotes passarem, ou não, de acordo com regras.  

Abordagens clássicas de configuração:

    O que não é expressamente proibido é permitido - proxy.
    O que não é expressamente permitido é proibido - firewall.

### Explique criptografia, seus algoritmos, para que serve e para quais requisitos servem?
É a arte e a ciência de esconder o objeto de uma comunicação de uma audiência não pretendida.  

Podem ser decifradas:  

- Criptografia simétrica:  
	A mesma chave serve tanto para criptografar quanto para descriptografar.  
	Criptografia bidirecional e melhor desempenho.  
	Maior preocupação é como transmitir a chave sem que seja exposta/vazada ao público.  
			
	    Ex: AES, DES, 3DES
	
- Criptografia assimétrica:  
	Um par de chaves é criado. A chave privada serve para criptografar enquanto a chave pública para descriptografar.  
	Impossível obter o par todo a partir de uma das metades.  
	A chave pública pode ser publicada.  
	Criptografia unidirecional.  
	Pior desempenho.  
			
	    EX: RSA, ElGamal, Diffie-Hellman
	
Não podem ser decifradas:  

- Hashs criptográficos.  
    Conhecidos como digestores.  
    Algoritmos de caminho único (impossível fazer caminho inverso).  
    Dada uma mensagem ‘m’ de qualquer tamanho obtém-se o código ‘f’ de tamanho fixo para qualquer ‘m’ através de uma função ‘H’:  

	> h = H(m).

	    Ex: MD3, MD5, SHA.  

Servem para os requisitos de CONFIDÊNCIA e INTEGRIDADE.  

### O que é assinatura digital?
A assinatura digital é um conteúdo cifrado transmitido junto com a mensagem para sua conferência.  

É criada pela chave privada de uma pessoa para permitir a autenticidade (INTEGRIDADE).  
Só pode ser verificada/decifrada pela chave pública parceira.  
Geralmente combinado com hashing criptográfico para reduzir seu tamanho.  

## Aula XI
### O que é VPN / túnel VPN?
Virtual Private Network.  
Forma de comunicação privada, através de canais públicos.  

As redes privadas virtuais são conexões criadas através da Internet ou através de redes públicas/privadas para a transferência de informações, de modo seguro, entre redes corporativas ou usuários remotos. Apresentam criptografia e interligam duas ou mais redes privadas através de um túnel via internet ou link público. 

### Explique túnel voluntário e túnel compulsório.
Túnel voluntário:  
- VPN entre duas máquinas.  
- O computador do usuário funciona como uma das extremidades do túnel e como cliente do túnel.  
- O túnel pode estar disponível ou ser criado sob demanda.  
- Os pontos finais sabem da existência do túnel.  
	
Túnel compulsório:  
- VPN entre duas redes.  
- O computador do usuário não funciona como extremidade do túnel, então desconhece sua existência.  
-  O roteador da rede (de um provedor) identifica que tal destino é via VPN apenas ao se comunicar.
-  Então encaminha pelo túnel, de forma transparente.