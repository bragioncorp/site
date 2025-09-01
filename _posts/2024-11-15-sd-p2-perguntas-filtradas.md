---
title: "SD P2 Perguntas"
excerpt: "SD P2 Perguntas"
categories:
  - Sistemas Distribuídos
tags:
  - Sistemas Distribuídos
  - Perguntas
  - Respostas

toc: true
---

# Aula 7

## O que são nomes? Qual sua relação com a transparência de localização?

Nomes descrevem entidades e referenciam endereços, usados na resolução de nomes.

Garantem transparência de localização pois ao mudar o ponto de acesso o nome continua o mesmo (servidor de nomes deve manter a referência atual dos pontos de acesso)).

## O que é LDAP? Quais são suas siglas e hierarquias?

LDAP (lightweight directory access protocol): implementação aberta desenvolvida para uso na Internet que opera na pilha TCP/IP, inspirada no modelo de serviço de diretórios X.500 DAP que opera na pilha ISO/OSI (implementação complexa).
	
A hierarquia é:

- (root)
- DC Domain Component
- C Country
- L Locality
- O Organization
- OU Organizational Unit
- CN Common Name

## Desenhe a hierarquia LDAP abaixo:

"No topo da hierarquia da Universidade de São Paulo (USP), no Brasil, está o Departamento de Física, que abriga o Servidor Central — essencial para gerenciar e distribuir dados de pesquisa entre pesquisadores e estudantes. Esse servidor centraliza a segurança e a eficiência na troca de informações dentro do departamento.

Conectados a ele, estão os hosts Sirius e Andromeda, ambos em São Paulo. Sirius (IP 143.107.251.45) armazena grandes volumes de dados experimentais, enquanto Andromeda (IP 143.107.251.46) é responsável pelo processamento de simulações e análises complexas. Juntos, esses hosts garantem acesso constante aos dados cruciais para as pesquisas, contribuindo para a excelência acadêmica do departamento."

![image](https://github.com/user-attachments/assets/4ce51489-66a7-4313-8870-94014bd9a290)

![image](https://github.com/user-attachments/assets/6bd25176-1a3f-4387-b3d4-cc655b45646f)


# Aula 8

## Explique o que é transação e como usa o commit e o rollback. Defina e explique ACID.

Transação é uma sequência definida de operações e eventos que podem usar recursos compartilhados e devem proteger o acesso simultâneo a estes. Ao ser iniciada, commit solicita que outros processos se comprometam com o primero, tendo um resultado permanente e/ou rollback discorda da situação e toda a transação é revertida ao ponto de partida.
	
ACID é uma das propriedades de uma transação.
- Atômica: transações são indiviseis.
- Consistente: o sistema deve ser mantido em estado consistente.
- Isolada: uma transação não pode interferir em outra transação.
- Durável: os efeitos de uma transação são permanentes.


## Explique o gerenciamento de transações X scheduler.

Gerenciamento de transações: garante atomicidade das transações, transforma primitivas em chamadas de escalonador e acessa diversos escalonadores.
	
Escalonador: controle da concorrencia e determina qual transação pode passar operações de leitura e escrita ao gerenciador de dados.

## O que é serialização e como isso pode usar o algortimo 2FL?

A Serialização impõe ordem de execução, isola transações simultâneas e garante que o resultado seja equivalente ao de uma execução sequencial.
	
O algoritmo de bloqueio em duas fases (2PL) pode ser utilizado para dar suporte à serialização já que funciona bloqueando um recurso sempre que uma transação precisa acessá-lo (growing phase) ou liberando o recurso quando não é mais usado (shrinking phase).

# Aula 9

## Defina disponibilidade e confiabilidade.

Disponibilidade: quanto do SD está disponível para ser usado imediatamente (estar operante).

Confiabilidade: quanto do SD pode operar de forma confiável.

## Forneça um exemplo de disponibilidade e confiabilidade.

Se um sistema parar por um milissegundo a cada hora -> disponibilidade será alta e confiabilidade baixa.

Se um sistema nunca falha, mas fica desligado duas semanas todo mês de agosto -> sua confiabilidade será alta e disponibilidade de apenas 96%.

## Defina defeito, erro e falha e apresente um exemplo de cada.

Falha: causa que originou o erro.  
Ex: ocorreu um problema na comunicação com o banco de dados durante o cadastro.

Erro: parte do estado de um SD originado por uma falha.  
Ex: dados incorretos de autenticação estão armazenados na memória do sistema.

Defeito: consequência de um estado de erro do SD (não cumpre promessa).  
Ex: sistema de login não autentica o usuário, mesmo com senha correta.

## Defina falhas transientes, intermitentes e permanentes e apresente um exemplo de cada.

Falhas transientes: falhas que ocorrem apenas uma vez e desaparecem.  
Ex: perda de sinal por alguns segundos ao usar streaming de vídeo.

Falhas intermitentes: não definem um padrão exato e são imprevisíveis.  
Ex: mau-contato de fios.
	
Falhas persistentes: não podem ser consertadas e implicam em danos irreparáveis.  
Ex: bugs, dano físico em hardware.

## Do que se trata o agrupamento de processos? Compare com TCP/UDP.

É uma organização para replicação de processos onde processos idênticos são agrupados e podem receber multicast por grupos dinâmicos.

Os grupos podem ser plano (processos têm papéis iguais e decisões coletivas) ou hierárquico (um processo será o eleitor e fará papel diferente dos demais).
	
Comunicações com o TPC geram falhas, mascaram falhas e geram problema com a abordagem ponto-a-ponto (um canal entre cada par).

O agrupamento de processos resolve isso com SRM (scalable reliable multicasting) onde só são comunicadas as mensagens faltantes, reduzindo a demanda de tráfego na rede.
	
## Explique 2FC.

Ocorre através de 2 fases.

A primeira é a fase de votação onde o coordenador envia uma mensagem 'VOTE_REQUEST' para os participantes. Os participantes podem responder 'VOTE_COMMIT' se estiverem preparados para fazer o commit local ou 'VOTE_ABORT' caso contrário.

A segunda é a fase de decisão onde o coordenador obtém os valores e responde a todos 'GLOBAL_COMMIT' se todos votarem a favor ou 'GLOBAT_ABORT' se apenas um votar em abortar.

Os participantes aguardam a resposta: se for 'GLOBAL_COMMIT' executam o commit local da transação e se for 'GLOBAT_ABORT' a transação local é abortada.

# Aula 10

## Defina confidência e integridade.

Confidência: a informação deve ser acessível apenas a quem for autorizado.

Integridade: as alterações na informação mantida por um sistema só podem ser realizadas das maneiras previstas e autorizadas.

## Liste os tipos de criptografia. O que assimetria e simetria? como ocorre a autenticação? O que é assinatura digital? E hashing?

Simétricas: possui uma chave, usada tanto para criptografar quanto descriptografar. O texto é criptografado com uma chave qualquer e é descriptografado com a mesma. Algoritmo é simples e de baixo custo computacional, melhor desempenho, problema é como enviar a chave única sem vazamento e é criptografia bidirecional. EX: DES, 3DES, AES, IDEA.

Assimétricas: possui duas chaves, pública (pode ser distribuida em públio) e privada (fica guardada em segredo com o dono). O texto é criptografado com a chave pública pelo destino e só pode ser descriptografado com a chave privada do mestre, ou vice-versa. Podem ser distribuídas livremente e seu algoritmo apresenta alto custo computacional (pior desempenho), é impossível obter uma chave a partir de outra e é criptografia unidirecional. Ex: RSA, Diffie-Helman, Elgamal.
	
Assinatura digital: conteúdo cifrado e transmitido junto com a mensagem para sua conferência. Usadas para garantir autenticidade da mensagem (integridade) e pode ser implementadas na comunicação de duas entidades junto com o algoritmo de chave pública, onde uma entidade assina sua mensagem com sua chave privada e depois com a chave pública da outra antes de enviar e, no processo inverso, a outra decifra primeiro com sua chave privada e depois com a pública da entidade que enviou, provando para a outra que ela é ela mesma.

Hashing criptográfico: funciona "digerindo" uma mensagem de qualquer tamanho e gerando um índice hash de tamanho fixo. É considerada criptografia de caminho único pois é computacionalmente impossível recuperar a mensagem.

## Explique o controle de acesso com ticket.

Um ticket de acesso assinado digitalmente é fornecido ao cliente que apresentará ao objeto de destino e este pode então confirmar a validade da autorização com o servidor e atender o pedido.

Essa estratégia reduz bastante a demanda pelo servidor para validação de acesso.

# Aula 11 e 12

## O que são stubs, skeletons e interfaces?

![image](https://github.com/user-attachments/assets/bb2b4109-dd27-49ad-a2cd-acef80d286d9)

- Stub: representação local que disponibiliza todos os métodos expostos pela interface do objeto remoto.

- Skeleton: implementação server-side do objeto distribuído.

- Interfaces: descreve os métodos que serão expostos pelos objetos distribuídos.

Esses conceitos são aplicáveis a muitas outras tecnologias de comunicação remota, como: CORBA, gRPC e SOAP.

- Para acessar métodos de um objeto distribuído o cliente deve utilizar a interface remota desse objeto presente no stub.

- O stub intercepta a chamada e a remete ao objeto que representa a implementação (skeleton) no servidor.

## Liste detalhadamente os passos de funcionamento das interface, stub e skeleton.

- 1 . A interface define os métodos que o cliente pode chamar.

- 2 . O stub recebe uma chamada para um método da interface, serializa os parâmetros e envia a requisição ao servidor.

- 3 . O skeleton recebe a requisição, desserializa os parâmetros, chama o método correspondete no servidor e serializa a resposta enviando ao cliente.

- 4 . O stub desserializa a resposta e retorna o resultado ao cliente.

## De que forma o stub empacota os parâmetros em invocações remotas de métodos?

O stub usa marshalling para serializar os parâmetros em um formato transmissível pela rede.

## Descreva, sucintamente, as principais diferenças entre as tecnologias de middleware: RPC, DCOM, CORBA e Java/RMI.

Diferenças entre RPC, DCOM, CORBA e Java/RMI:

- RPC: Simples, orientado a chamadas de função, linguagem e plataforma dependentes.

- DCOM: Extensão do COM da Microsoft, usa protocolos proprietários, dependente de Windows.

- CORBA: Padrão multiplataforma e multilíngue, usa IIOP para comunicação.

- Java/RMI: Específico para Java, usa serialização de objetos.

## Compare e classifique: RPC, RMI, DCOM, CORBA, WS (WebServices).

RPC: remote procedure call, comunicação através de stubs cliente (tratam passagem de argumentos e comunicação) e server (passam chamadas locais a procedimentos do servidor) - transparência: empacota e desempacota parâmetros para serem transmitidos na rede e converte representação.

RMI: remote method invocation, servidor define interface para acesso remoto e cliente localiza servidor através de nomes além de que a chamada stub faz comunicação transparente com o skeleton e empacota os parâmetros.

DCOM: distributed componente object model, servidor fornece objetos em tempo de execução em interfaces e cliente chama os métodos do server através de um objeto proxy.

CORBA: common object request broker architecture, independente de linguagem e plataforma, conhecida como ORB localiza objetos implementados, prepara para atender requisições e comunica requisições e respostas.

WS: web service, apresenta interoperabilidade, baseados em padrões abertos, uso do XML, abrangência e alcançabilidade.

## Defina Web Services e apresente suas principais características.

Sistemas baseados em XML (SOAP/REST) para comunicação entre aplicações, independentes de linguagem e plataforma.

## Descreva uma vantagem que o uso de Web Services apresenta frente a cada uma das seguintes tecnologias: DCOM, RMI, CORBA. Justifique cada uma.

Vantagens de Web Services sobre DCOM, RMI e CORBA:

- DCOM: Independência de plataforma (não restrito ao Windows).
- RMI: Interoperabilidade entre diferentes linguagens, não apenas Java.
- CORBA: Menor complexidade e maior compatibilidade com sistemas modernos via HTTP.

## Quais são os dois tipos de transações suportadas por Web Services?

São as transações atômicas similar a CORBA Object Transaction Service (CORBA OTS) ou transações distribuídas de longa duração.
