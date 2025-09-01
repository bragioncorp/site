aula 1

explique o que desafio de transparência e seus tipos.

	visa esconder os detalhes específicos do sistema (visão de sistema único).
	
	de acesso:
	permite que recursos locais e remotos sejam acessados por operações iguais e esconde diferenças de representação de dados.
	
	de localização:
	esconde detalhes de onde o recurso está.
	
	de concorrência:
	permite o compartilhamento de um recurso concorrido por diversos usuários sem que haja interferência.
	
	de replicação:
	permite duplicação de informação para aumentar a disponibilidade e desempenho, o desafio é manter o sincronismo.
	
	de falha:
	esconde a ocorrência de falhas.
	
	de mobilidade:
	permite que um recurso seja movido para outro local durante o uso.
	
	de desempenho:
	permite a reconfiguração do sistema para melhorar o desempenho à medida que cargas variam.
	
	de escalabilidade:
	permite aplicativos se expandir sem alterar suas estrutra ou algoritmos.
	

explique interoperabilidade e portabilidade.

	interoperabilidade é a capacidade de sistemas diferentes (fornecedores diferentes) trabalharem juntos e trocarem informações (funcionar em conjunto).

	portabilidade é a capacidade do software ser executado em diferentes plataformas (SO e hardware) ou com mínimas modificações (software para A roda em B com interfaces de A).


aula 2

conceitue o middleware (o que é e ordem cornológica).

	implementam uma camada adicional de software que esconde parte da heterogeneidade das plataformas dos computadores e também oferece transparência de distribuição.
	colocado acima do SO e abaixo das aplicações.
	
	ordem cornológica:
		baseado em sistemas de arquivos:
		todos os recursos do sistema eram representados em arquivos.
		
		baseado em chamadas remotas:
		esconde a complexidade de comunicação através de rede, chamada a procedimento stub que é trocada por procedimento remoto.
		
		baseado em objetos distribuidos:
		cada objeto remoto implementa uma interface que esconde os detalhes dos usuários, as mensagens são interceptadas pelo middleware e transmitidas pela rede localmente até o objeto que implementa.
		
		baseado em documentos/serviços distribuidos:
		cada recurso possui uma referência única (web - URL).


defina multiprocessadores e multicomputadores, qual é fortemente ou fracamente acoplado e o que significa.

	multicomputadores:
	múltiplos computadores autônomos e cada um possui seu próprio processador, memória e SO, conectados por uma rede de forma independente.
	fracamente acoplado pois há uma baixa interdpendência entre os componentes e pouca ou nenhuma necessidade de coordenação contínua.
	
	multiprocessadores:
	múltiplos processadores que compartilham um pedaço da memória em comum e utilizam o mesmo SO.
	fortemente acoplado pois há alto nível de interdependência entre os componentes e necessidade de coordenação contínua.


liste os serviços oferecidos pelo middleware.

	facilidades de comunicação:
	transparência de acesso aos serviços de comunicação da rede.
	
	serviço de nome:
	nome é uma referência independente do endereço de rede e provê transparência de localização, permitindo escalabilidade e replicação.
	
	persistência:
	serviço transparente de armazenamento de dados integrados ao SGBDs.
	
	transações distribuidas:
	levam o sistema a um estado consistente, tanto commit quando rollback.
	
	segurança:
	provê facilidades para autenticação de usuários, controle de acesso, encriptação e assinatura de mensagens.


explique persistência X transiência. sincronismo X assincronismo.

	comunicação persistente:
	mensagens são armazenadas pelo serviço de comunicação mesmo que um dos comunicantes esteja indisponível, permitindo que emissor e receptor operem em tempos distintos.
	
	comunicação transiente:
	mensagens mantidas na memória das partes comunicantes e para haver comunicação o emissor e receptor devem estar operantes. após concluído e confirmado, o emissor pode apagar a mensagem memória.


explique troca de mensagem.

	mensagens são unidades básicas de comunicação (carregam dados e comunicam eventos).
	formas de estabelecer sincronismo:
		bloqueio do emissor até o buffer estiver disponível.
		bloqueio do emissor até a mensagem ser enviada.
		bloqueio do emissor até a mensagem ser recebida.
		bloqueio do emissor até a mensagem ser respondida.


aula 3

conceitue cliente-servidor

	cliente: mestre - solicita conexão e serviço ao servidor.
	
	servidor: escravo - aguarda solicitações do cliente e devolve a resposta.


demonstre um exemplo de códigdo presente no cliente, no servidor, chamads bloqueantes, no tcp e udp



defina as principais primitivas

	SOCK_STREAM
	socket()			cria um descritor de socket no cliente e no servidor.
	bind()				associa o socket a um IP.
	listen()			coloca o servidor em modo de espera para conexões.
	accept()			o servidor espera por uma conexão, BLOQUEANTE (até o cliente conectar).
	connect()			inicia uma conexão com o servidor, BLOQUEANTE (até estabelecer conexão).
	read()/write()		troca de dados no cliente e servidor, BLOQUEANTE (até dados serem lidos e escritos).
	close()				fecha o socket.
	
	SOCK_DGRAM
	socket()			cria um descritor de socket no cliente e no servidor.
	bind()				associa o socket a um IP.
	sendto()			envia um pacote para um destino.
	recvfrom()			recebe um pacote de um destino, BLOQUEANTE (até receber o pacote).
	close()				fecha o socket.


liste as principais funções de sockets

	Comum:
	cria um descritor de socket
		int socket(int domain, int type, int protocol)

	registra um socket a um número de porta
		int bind(int sockfd, struct sockaddr *my_addr, socklen_t addrlen)

	fecha e libera o socket
		int close(int sockfd)


aula 4

defina 'relógios físicos' e explique como relógios do computador são representados.

	


comente sobre sincronização ao tempo natural. existem problemas?

	tempo pela humanidade (rotação determina o dia e translação determina o ano).
	tempo por relógios atômicos (utilizam átomo de césio, informam ao BIH e este calcula os valores e produz o TAI - 100ns de erro por ano)
	
	problemas: tempo de rotação da Terra aumentou e o referencial marcará horários incompatíveis para os períodos do dia.
	solução: UTC (Universal Coordinated Time) e NIST (National Institute of Standard Time).


o que é UTC? onde é usado?

	UTC é o padrão de tempo internacional usado para sincronizar relógios em todo o mundo. Combina o tempo atômico com correções baseadas na rotação da Terra, garantindo precisão e é usado para sincronização através do algoritmo de Cristian.


explique o ajuste de relógios nos algorimos de Cristian e Berkeley.

	Cristian:
		receptor WWV.
		uma máquina X assumirá o papel de time server para as demais.
		as máquinas participantes pedem a hora atual para o servidor através de uma mensagem.
		o servidor responde com o valor C UTC
		
		problemas:
		o tempo de resposta (RTT - round trip time) da rede pode se alterar.
		um relógio só pode registrar o acréscimo do tempo.

	Barkeley:
		não usa receptor WWV.
		usa servidor monitor que solicita o registro do tempo para cada máquina envolvida.
		o servidor computa a média de todos os registros e envias para as maquinas ajustarem seus relógios.


explique happens-before e seu usando em lamport timestamps.

	happens-before define a ordem casual entre eventos: se A ocorre antes de B, então A -> B.
	Lamport Timestamps garantem que se A -> B então o timestamp de A será menor que B e o inverso nem sempre é verdadeiro.


liste e explique os algoritmos de eleição do coordenador Bully e Anel.

	Bully:
	ideia que os processos estão querendo se tornar coordenadores.
	quando um processo 'P' detecta que o coordenador não está operante, 'P' inicia uma eleição.
	- 'P' encaminha uma mensagem 'ELECTION' a todos os processos com números maiores.
	- Se ninguém responder, 'P' vence a eleição e se torna coordenador.
	- Se um processo (com número maior) responder (mensagem OK) ele assume a dianteira e reinicia em 1 (enfrenta outro).
	- O processo que vencer a eleição encaminha uma mensagem COORDINATOR a todos os processos e assume o papel de coordenador.
	- Se um processo que estava parado retorna à execução inicia uma nova eleição.
	
	Anel:
	O anel representa a ordenação sequencial dos processos
	- Quando um processo detecta que o coordenador está inoperante, ele encaminha uma mensagem 'ELECTION' ao seu sucessor contendo seu próprio número de processo.
	- Cada processo na sequência insere seu número na lista e torna-se candidato.
	- Quando a mensagem chegar novamente no emissor, verifica qual processo tem maior número.
	- Constrói uma mensagem 'COORDINATOR' para informar a todos quem venceu a eleição e assumirá a função de coordenador.


dada a seguinte configuração de um relógio:
	ƒcristal = 1MHz
	Holding register = 50000
	
	a) quanto vale, em segundos, cada clock tick?
	b) para a configuração acima, assuma que o tempo inicial (zero do relógio) foi atribuído para
14/09/2020, às 0h. Considere a data e hora atuais: 14/09/2020 – 9h15min0s. Quantos clock ticks
foram acumulados em Cp(t)?

	ƒcristal = 1MHz
	Holding register = 50000

	a)	50k = clock tick
		1MHz = 1000000 Hz
		
		ƒcristal/holding register = 1000000/50000 = 20 clock ticks por segundo (ctps).

		1/ctps = 1 / 20 = duração em segundos -> 0.05 segundos.
	
	b)	tempo inicial:	14/09/2020 - 0h
		atual:			14/09/2020 - 9h15min0s

		converter p segundo
		9 * 60 * 60 + 15 * 60 = 33300 seg
		
		clock ticks acumulados em Cp(t):		
		seg * clockticks = 33300 * 20 = 666000 clockticks