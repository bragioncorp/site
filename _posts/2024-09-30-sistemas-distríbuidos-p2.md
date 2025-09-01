---
title: "Sistemas Distribuídos - Resumão para P2"
excerpt: "Resumo Sistemas Distribuídos"
categories:
  - Sistemas Distribuídos
tags:
  - Sistemas Distribuídos
  - Resumo
  - Teoria

toc: true
---

# Aula VII

## Por que sistemas distribuídos usam resolução de nomes?

Porque oferecem:  
- Compartilhamento de recursos  
- Identificação única de entidades  
- Referência de localidades  

## O que é resolução de nomes?

Processo de identificação de uma entidade através de seu nome.

Geralmente realizada através da consulta a um servidor de nomes.

## O que são nomes?

Descrevem entidades: computadores, usuários, impressoras…

Referenciam endereços: endereço é um tipo especial de nome que se refere a um ponto de acesso de uma entidade.

Identificador: referência única de uma entidade.

Fornecem transparência de localização:
- um ponto de acesso pode ser modificado, mas seu nome mantido para o sistema.
- o servidor de nomes deve manter a referência atual dos pontos de acesso.

## O que são Names Spaces

Forma como os nomes estão organizados (grafos).

![image](https://github.com/user-attachments/assets/a45f09dd-59cd-44a9-9f5b-7b5d749ce273)

## Explique a organização hierárquica

Existem 3 níveis.

### Nível global

Nós de mais alto nível (nó raiz e seus filhos diretos).  
Estrutura normalmente estável (modifica-se muito pouco).  
Descrevem organizações ou grupos de organizações.  

### Nível administrativo

Abaixo do nível global.  
Alteram-se com pouca frequência.  
Referenciam grupos de entidades de uma mesma organização ou unidade administrativa (exemplo: departamentos de uma organização).  

### Nível gerencial
 
Alteram-se com maior frequência.  
Representam entidades, como hosts ou sistemas de arquivos.  

## DNS

Domain Name System - serviço de nomes da Internet.

![image](https://github.com/user-attachments/assets/68a17f1e-e736-48c7-970b-72b70fb2b206)

## Resolução de nomes

### Resolução iterativa

O nome é resolvido através de diversas iterações de consulta, partindo do nível global ao nível gerencial.

Ex:

![image](https://github.com/user-attachments/assets/fe600bae-f92d-4970-a203-45df41c6ec2b)

ftp:// -> name space -> porta aplicação.  
ftp.cs.vu.nl -> DNS host (IP).  
/pub/globe/index.txt -> caminho FS.  

## Servidores de nomes

As implementações mais difundidas são:

- DNS (Domain Name System): instituído pela RFC 1034, é o serviço de nomes padrão para a Internet.
- LDAP (Lightweight Directory Access Protocol): implementação aberta inspirada no modelo de serviço de diretórios X.500 DAP para uso na Internet.
- NDS (Novell Directory Services): implementação do serviço de diretórios da Novell, baseada no X.500 DAP.
- Active Directory: implementação padrão do LDAP pela Microsoft.

## X.500 DAP ( Directory Access Protocol)

Padrão da ISO/ITU que define um modelo independente de plataforma para o serviço de diretórios.

Diretório: banco de dados com informações sobre objetos e entidades, baseadas em atributos e organizadas em forma de árvore.

- DIB (Directory Information Base)  
Banco de dados com os registros do serviço de diretório.  

- DIT (Directory Information Tree)  
Define a organização hierárquica dos objetos  

- Objetos  
Descritos pelas entradas no diretório e possuem atributos  

## Hierarquia X.500

Diferentes classes para objetos, para cada nível  

(Root)  
DC Domain Component  
C Country  
L Locality  
O Organization  
OU Organizational Unit  
CN Common Name  

Regras de acesso (ACL – access control lists)  
São definidas entre objetos, através de seus atributos

## O que é LDAP?

Lightweight Directory Access Protocol.

Desenvolvido inicialmente para ser cliente do X.500.  

O X.500 impunha uma implementação complexa de protocolo, para
operar sobre a pilha ISO/OSI.

O LDAP foi adaptado para operar sobre a pilha TCP/IP e tornou-se um
padrão de fato para a Internet.

Sua versão 3 é descrita pela RFC 2251

## Exemplo de entrada LDAP

![image](https://github.com/user-attachments/assets/6e46416d-f0d2-4b97-b8ff-489560bd91d7)

## Exemplo de hierarquia LDAP

![image](https://github.com/user-attachments/assets/8894736f-1469-44d3-a55b-2183ef29bf80)

## O que é LDIF?

LDAP Data Interchange Format (RFC 2849).

Formato de intercâmbio de informações para o LDAP.

Descreve o diretório e suas entradas em formato texto.

Sintaxe:

![image](https://github.com/user-attachments/assets/6b3b56af-9581-436e-bd57-f2cc5c1c7f30)

## Exemplo LDIF com 2 entradas

![image](https://github.com/user-attachments/assets/3902b9b4-00c9-4f4d-a19e-b260bbb274ed)

# Aula VIII

## O que é transação distribuída?

É uma sequência bem definida de operações e eventos que podem fazer uso de diversos recursos compartilhados.

- Protege o acesso simultâneo a recursos compartilhados entre processos concorrentes.

- Permite o processo acessar e modificar múltiplos itens de dados como uma operação atômica

- Se um processo desistir no meio da transação tudo deve ser reestabelecido ao ponto inicial antes da transação.

## Como funciona o modelo de transações?

Abstraído do mundo dos negócios.

Qualquer processos pode anunciar o início de uma transação.

O processo que iniciou a transação pode:

- Solicitar que todos se comprometam com o trabalho (commit).

- Situação revetida caso um processo discorde (rollback).

## Quais são as primitivas de transações

![image](https://github.com/user-attachments/assets/d17a19c9-686e-4d8a-a868-86a68853fa5a)

Escopo da transação:
- BEGIN_TRANSACTION e END_TRANSACTION
- Operações entre elas formam o corpo da transação

Todas as operações do corpo da transação devem ser executadas, ou
nenhuma deve ser executada

## Explique rapidamente as propriedades de transações

"tudo ou nada" -> principal propriedade, que possui quatro qualidades (ACID).

- Atômica: transações são indivisíveis.
- Consistente: o sistema deve ser mantido em estado consistente.
- Isolada: uma transação não pode interferir em outra transação.
- Durável: os efeitos de uma transação são permanentes.

## Classificação de transações

### Flat Transactions

Uma série de operações que satisfazem as propriedades ACID.

Sua limitação é não permitir que resultados parcias sejam "commited" ou mesmo "abortados".

### Transações aninhadas

Podem ser aninhadas através da definição de sub-transações (mais altas podem criar foks novos para os filhos rodarem).

Quando uma transação inicia-se:

- recebe uma cópia privada de todos os dados de todo o sistema para manipular como quiser.

- Se a transação é abortad seu universo privado é descartado
- Se ela chega ao commit seu universo privado sobrescreve o do pai.

### Transações distribuídas

Vista como uma transação flat e indivisível que opera dados distribuídos.

Principal problema é definir algoritmos separados para manipular o controle de acesso aos dados e realizar (commit) a transação.

![image](https://github.com/user-attachments/assets/5302590a-aea2-4655-bc9a-0de30782dc69)

## Explique a implementação de transações

### Espaço privado

Quando um processo inicia uma transação, recebe um espaço privado de trabalho.

- Se prever o acesso a diversos arquivos, copiar tudo para seu espaço privado pode ser impossível ou pouco aconselhável.
- Se o processo apenas fará leitura em um arquivo (sem alterá-lo), não precisará de uma cópia privada.
- Se necessitar escrever em um arquivo, o processo pode manter em sua área privada apenas o mapeamento (índice) dos blocos do arquivo.
- Dessa forma, fará a leitura dos blocos e, se alterar algum deles, somente estes serão alterados no disco.

### Writeahead log

Alterações a serem realizadas em um arquivo são anotadas em um registro histórico.

Somente depois de confirmada a gravação do log que a alteração pode ser realizada no arquivo.

Ex:

![image](https://github.com/user-attachments/assets/442cdd8d-e3e4-4ab2-b5b0-a82efe02cc02)

- Todas as alterações sofridas em estruturas de dados (ou outros recursos) do sistema são armazenadas no registro histórico.

- Se uma transação tiver que ser abortada antes de seu fim, todas as alterações registradas (efetuadas por suas operações) podem ser desfeitas e o estado inicial das estruturas (e recursos) restabelecido (rollback)

## Controle de concorrência

Trata dos requisitos de consistência e isolação.

### Consistência

Permitir que diversas transações executem simultaneamente acessos a uma coleção de itens de dados, mantendo-os em estado consistente.

Execução sequencial das transações sobre o conjunto de dados.

### Escalonador (scheduler)

Responsável pelo controle da concorrência.

Determina qual transação tem permissão para passar operações de leitura ou escrita ao gerenciador de dados (data manager) a cada momento.

### Isolação e Consistência

Podem ser garantidas pelas operações individuais de leitura e escrita realizadas pelo gerenciador.

### Gerenciador de transações (transaction manager)

Responsável por garantir a atomicidade das transações

Processa as primitivas das transações, transformando-as em chamadas ao escalonador.

![image](https://github.com/user-attachments/assets/7fe172fc-edc1-4019-a7c6-72fba1008ef6)

Pode ser utilizado para acessar diversos escalonadores em um ambiente distribuído.

![image](https://github.com/user-attachments/assets/e6ce33c1-e10c-4bdd-8ad6-dbb066c91238)

## Serialização

Impõe uma ordem de execução, isolando transações da execução simultânea e garantindo a execução sequencial de transações (só inicia se outra encerrar).

Duas abordagens p/ solução

Pessimista é mais utilizada e admite que problemas de concorrência irão ocorrer

Utiliza o bloqueio dos recursos (locking) como forma preventiva de evitá-los.

Ex:

![image](https://github.com/user-attachments/assets/5aa8d65d-6756-48cd-912f-0170c8bbf26c)

## Bloqueio em duas fases

Two-phases locking

- Quando um processo necessita de um recurso solicita o bloqueio do mesmo.

- Quando prevê não mais utilizá-lo, realiza sua liberação.

Sendo assim, o algoritmo prevê duas fases distintas:

- growing phase: fase onde ocorre o bloqueio de recursos pelo  processo.

- shrinking phase: fase na qual os recursos são liberados pelo  processo.

![image](https://github.com/user-attachments/assets/375bcd93-34c1-4efe-a11b-b7a95a631560)

![image](https://github.com/user-attachments/assets/5096924a-1fb8-4534-8cbe-468beb11c593)

## Gerenciamento de transações em EJB

Controle de transações resumi-se à demarcação de transações (quando será iniciada e concluída).

Várias formas de demarcar transações (cliente - comuns, servlets, beans - ou servidor - no container, declarações no DD, ou no bean, APIs como JTA, JDBC ou JMS).

## Estailo de demarcação

### BMT (Bean-Managed Transactions)

Total controle sobre o início e o fim das transações.

Nas outras modalidades é necessário ter todo o bean dentro (ou fora) de uma transação.

### CMT (Container-Managed Transactions)

Maior simplicidade.

Mais seguro: evita a introdução de código que pode provocar deadlock e outros problemas similares.

Tunnig de transações sem alterar uma linha de código.

### Demarcadas pelo cliente

Vantagem: controle em relação a falhas de rede.

Desvantagem: transação muito longa - ineficiente.

## CMT – Container Managed Transactions

Controle de transações totalmente gerenciado pelo container.

Não permite o uso de métodos commit() e rollback() de java.sql.Connection ou javax.jms.Session dentro do código.

Única forma de controlar transações em Entity Beans.

## Políticas transacionais - atributos

Os vetores suportados são:

NotSupported
- Indica que o método não suporta transações.

Supports
- Indica que o método suporta transações.

Required
- Indica que o escopo de uma transação é requerido pelo método.

RequiresNew
- Indica que o método requer uma nova transação.

Mandatory
- Indica que o método só pode ser chamado no escopo de uma transação do cliente.

Never
- Indica que o método nunca pode estar dentro de uma transação.

## Serviço de transações

Servidores J2EE oferecem serviço de transações distribuídas
CORBA: Object Transaction Service (OTS).

– Pode ser obtido através do serviço de nomes (via JNDI ou COS Naming).

Clientes também podem obter o serviço de transações do recurso que estão utilizando (se houver).

– Bancos de dados (através de JDBC).
– Sistemas de messaging (através de JMS).

Para ter acesso a esses serviços, existem APIs.

– JDBC ou JMS, para serviços do recurso utilizado.
– JTS ou JTA, para acesso ao OTS (distribuído).

Beans também podem realizar controle declarativo.

## JTS e JTA

JTS - Java Transaction Service  
é um mapeamento java-CORBA da especificação Object Transaction Service.

- Usado por fabricantes de containers.

JTA - Java Transaction API  
é uma especificação de interfaces para o sistema de transações.

- Suporte por parte do container é obrigatório.

## Tipos de Beans 

### Transientes (session beans)

- Fornecem suporte à sessões de clientes, durante transações com servidores de aplicação Java EE.

### Mensagens (message-driven beans)

- Realizam a comunicação via troca de mensagens entre cada parte que compõe o sistema distribuído

### Persistentes (entity beans)

- Representam os dados armazenados (persistidos) em servidores de
bancos de dados

## Session Beans

Encapsulam a lógica do negócio.

O session bean realiza o trabalho para o cliente, escondendo a complexidade de executar as tarefas de negócio no lado servidor

Tipos de session beans

### Stateful Session Beans

- As variáveis de instância representam uma única sessão do cliente
- São transientes, ou seja, são descartados quando a sessão terminar

### Stateless Session Beans
- O estado (valores de instância) não é retido depois de uma  chamada.
- Estado descartado assim que o método termina

### Singleton Session Beans
- São instanciados um por aplicação e existem enquanto ela executar.
- Podem ser compartilhados entre diversas sessões de clientes.

## Message-drive Beans

Um message-driven bean é um EJB que permite aplicações Java EE processarem mensagens assíncronas.

- Geralmente atua como um JMS message listener (Como um event listener, mas recebe mensagens no lugar de eventos).

- Podem também processar outros tipos de mensagens, além de JMS.

- Diferem-se dos session beans pois não são acessados via interfaces.

- Operam transações de múltiplos clientes e não retêm estados (stateless).

# Aula IX

## Requisitos de dependabilidade em SD

Disponibilidade: mede quanto o SD está pronto para ser usado imediatamente, probabilidade de um SD estar opertante.

Confiabilidade: mede quanto tempo um SD pode operar continuamente, sem a ocorrência de falha.

Segurança: capacidade de um SD nçao gerar algo catastrófico quando falhar na operação.

Manutenabilidade: facilidade de se reparar um SD ao apresentar falha. Boa manutenabilidade implica em maior disponibilidade.

## Exemplo disponibilidade VS confiabilidade

Se um sistema parar por um milissegundo a cada hora -> disponibilidade será alta e confiabilidade baixa.

Se um sistema nunca falha, mas fica desligado por duas semanas todo mês de agosto -> sua confiabilidade será alta e disponibilidade de apenas 96%.

## Defeito VS Erro VS falha

Defeito: consequência de um estado de erro do SD (não cumpre promessa).

Erro: constitui parte do estadp de um SD originado por uma falha.

Falha: trata-se da causa que originou o erro.

## Tipos de falhas

Transientes: falhas que ocorrem apenas uma vez e então desaparecem.

Intermitentes: não definem um padrão exato de ocorrência e são imprevisíveis.

Permanentes: não podem ser consertadas e normalmente implicam em danos irreparáveis em componentes.

## Modelos de falhas

Falha por quebra (crash): abrupta, normalmente associadas ao hardware e nada pode ser feito senão reiniciada.

Falha por omissão: quando um servidor falha ao responder uma requisição.

- Omissão da requisição: o servidor nem chega a receber a solicitação do cliente (perdida).

- Omissão da resposta: a resposta já foi perdida ou nem ter sido encaminhada à rede (servidor acha que enviou).

Falha de sincronismo: resposta em ritmo alterado pelo servidor (responder cedo ou tarde demais).

Falha na resposta: resposta errado do servidor, pode ser por valor incorreto ou falha de transição de estados (reação inesperada).

Falha arbitrária: servidor produz resposta que nunca deveria ser produzida, geralmente gerado por código malicioso e pode ser confundida com outras falhas.

## Redundância e resiliência de processos

Redundância de informação: uso de informação extra para recuperar erros em dados (código Hamming).

Redundância de ocorrência: ação pode ser repetida durante a execução de uma transação, caso necessário (TCP).

Redundância física (hardware ou software): adição de equipamento ou processos extras que permitem o sistema suportar o mau funcionamento de algum componente individual.

## Agrupamento de processos

Processos idênticos são agrupados e podem receber mensagems multicast (grupos dinâmicos), garantindo organização e replicação.

Podem ser dinâmicos e um processo pode participar de mais de um grupo.

Estrutura de um grupo

- Grupo plano: processos têm papéis iguais e decisões são tomadas coletivamente.

- Grupo hierárquico: um dos processos é considerado coordenador e fará um papel diferente dos outros.

## Comente o contexto dos protocolos TCP e UDP, usados em comunicações inter ou intragrupos de processos? Por quê?

TCP: garante confiabilidade na comunicação entre processos para garantir a ordem de entrega, adequado para comunicações intergrupos onde processos podem estar geograficamente distribuídos e necessita retransmitir pacotes perdidos e controlar o congestionamento.

UDP: adequado para comunicações com baixa latência, alta eficiência, a perda de pacotes é tolerada (confiabilidade baixa) e são usadas em comunicações intragrupo em redes locais ou quando se trata de enviar mensagens para muitos processos de forma rápida com menos overhead.


![image](https://github.com/user-attachments/assets/6153cdeb-591f-4dcc-879e-235ecfc1bd94)

## Controle de grupo

Modelo centralizado: servidor de grupos administra os grupos (ponto único de falha do SD) e a replicação é baseada em um principal (primary-based - estruturação hierárquica - coordenador representa a comunicação com outros processos).

Modelo distribuído: todos os processos do grupo mantém informações sobre ele (pedidos devem ser enviados a todos e é 'k fault tolerant') e possui replicação de escrita.

## comunicação confiável

Permite enviar/tratar falhas por quebra, omissão, sincronismo ou arbitrária.

Comunicação ponto-a-ponto com TCP, protocolo de transporte confiável e mascara falhas (retransmite falhas perdidas).

Problemas com TCP: a conexão pode se encerrar abruptamente

## SRM

Scalable Reliable Multicasting

Só são comunicadas as mensagens faltantes, o que já reduz a demanda de tráfego na rede e evita que mais de um membro do grupo reclame a mesma mensagem.

![image](https://github.com/user-attachments/assets/812c54ed-573d-4545-85c6-7ee6e2e21712)

## Estratégia hierárquica

O coordenador de cada subgrupo é responsável por comunicar eventuais mensagens não recebidas pelos membros do grupo.

![image](https://github.com/user-attachments/assets/4efb4179-d224-4be5-ac8b-ebc152614ea1)

## Comunicação multicast

### Multicast atômico

Todos devem receber a mensagem.

Sincronismo virtual

- A camada de comunicação do SD deve segurar a mensagem até que todas as suas parceiras notifiquem o recebimento.

- A partir daí, todas as entidades podem passar a mensagem para a camada superior (aplicação).

![image](https://github.com/user-attachments/assets/5e44c26a-34a9-49b2-9885-df0259ae4db6)

### Ordenação de mensagens multicast

4 abordagens.

- Multicast desordenado confiável: garante-se que as mensagens cheguem, mas não garante a ordem.

- Multicast ordenado em filas (FIFO) confiável: a camada de comunicação é obrigada a entregar as mensagens na mesma ordem que forem enviadas.

- Multicast ordenado por causalidade e confiável: a entrega das mensagens mantém a relação de causalidade entre as diferentes operações do sistema.

- Multicast totalmente ordenado: independentemente da estratégia utilizada para encaminhamento, exige que as mensagens sejam entregues a todos os membros na mesma ordem.

## Commit distribuído

Um problema para commit em SD é garantir que uma operação seja realizada por cada membro do grupo, ou nenhum deles.

A solução é eleger um coordenador que ordena que os processos realizem, ou não, as operações em questão.

## Commit em duas fases

Garante que uma operação seja realizada por cada membro do grupo, ou nenhum deles.
Deve eleger um coordenador que ordena que os processos realizem ou não.

Ocorre através de 2 fases.

A primeira é a fase de votação onde o coordenador envia uma mensagem 'VOTE_REQUEST' para os participantes. Os participantes podem responder 'VOTE_COMMIT' se estiverem preparado para fazer o commit local ou 'VOTE_ABORT' caso contrário.

A segunda é a fase de decisão onde o coordenador obtém os vaores e responde a todos 'GLOBAL_COMMIT' se todos votarem a favor ou 'GLOBAT_ABORT' se apenas um votar em abortar.

Os participantes aguardam a resposta, se for 'GLOBAL_COMMIT', executam o commit local da transação e se for 'GLOBAT_ABORT', a transação local é abortada.

![image](https://github.com/user-attachments/assets/98b2bdcb-ba77-4376-874f-8246e0d21399)

# Aula 10

## Conceitos básicos

Segurança em Sistemas Distribuídos

- Relacionada à dependabilidade (tolerância a falhas) que o sistema pode oferecer.

Parâmetros adicionais relacionados à informação

- Confidência: a informação deve ser acessível apenas a quem for autorizado.
- Integridade: as alterações na informação mantida por um sistema só podem ser realizadas das maneiras previstas e autorizadas.

## Ameaças à informação

Interceptação

- Acesso não autorizado à informação.
- Cópia ilegal da informação.

Interrupção

- Quando a informação torna-se inacessível.
- Pode ser gerada pela indisponibilidade de um serviço (ex.: DOS – Denial of Service) ou pela destruição dos dados.

Modificação

- Troca não autorizada dos dados ou alteração em serviços fora das especificações originais.
- Em redes de comunicação, a informação pode ser primeiramente interceptada e depois modificada.

Fabricação

- Criação de dados ou de atividades que não deveriam existir

## Mecanismos

Encriptação (cifragem)

- Produção de cifra a partir dos dados

  Para confidência: mensagens indecifráveis por terceiros  
  Para integridade: assinaturas digitais para conferência  

Autenticação

- Verifica a identificação solicitada ao usuário (ou aplicação)
- Normalmente apoiada por conferência de senhas

Autorização

- Estabelece as formas de interação com o sistema

  Regras de acesso (permissões)  
  Diferentes usuários podem ter diferentes perfis  

Auditoria

- Avaliação dos efeitos dos mecanismos de proteção de um sistema

  São verificados registros históricos (arquivos de log, por exemplo), que descrevem as atividades de usuários no sistema  

## Foco de controle

![image](https://github.com/user-attachments/assets/1c0e2663-3904-4797-8b5c-9c7313260215)

## Criptografia

É  a arte e a ciência de esconder o objeto de uma comunicação de uma audiência não pretendida.  
	
### Permitem decifrar:

Chave simétrica:

    + Criptografia bidirecional.
    + Melhor desempenho.
    - Como enviar a chave?

C = Eke(P)  
P = Dkd(C)  
Ke = Kd = Ks  

> Ex: DES, 3DES, AES, Blowfish.
			
Chave assimétrica:

Par de chaves único.  
Publicar com certificado.  

Confidência: Ke+ (Kd-)  
Integridade: Kd+ (Ke-)  
			
	+ Impossível obter o par, a partir de uma.
	+ Publicação de uma das chaves.
	- Criptografia unidirecional.
	- Pior desempenho.

Ke != Kd

> Ex: RSA, ElGamal, Diffie-Hellman

### Não permitem decifrar:

Hashs criptográficos.  
"caminho único".  
Hashs - digetores.  

Ex: MD3, MD5, SHA.

## Formas de ataque

![image](https://github.com/user-attachments/assets/bfb6e36e-1bf4-4881-a0d9-d7a0ae12b2eb)

Intruso passivo

- Apenas intercepta e obtém a mensagem.
- A encriptação deve garantir que a mensagem não possa ser facilmente decifrada pelo intruso.

Intruso ativo (alteração)

- Obtém a mensagem e a altera.
- Isso é mais difícil, pois deve interceptar, decifrar e novamente cifrar a mensagem e, para isso, possuir a chave K.

Intruso ativo (fabricação)

- Tenta criar mensagem falsa.
- Só conseguirá fazê-lo se possuir a chave K.

## Chaves de encriptação e algoritmos

Pode-se afirmar que a qualidade de um algoritmo criptográfico
depende muito da chave utilizada

- Os algoritmos criptográficos são conhecidos e têm código aberto.

Classificação de algoritmos pela chave

- Chave simétrica.
- Chave assimétrica (ou pública).

Classificação dos algoritmos quanto à decifragem

- Permitem a recuperação da mensagem original.
- Não permitem: são ditos “de caminho único” (one-way functions), ou digestores de mensagens.

## Algortimos de chave simétrica

Uma mesma chave é utilizada para cifrar e decifrar

Algoritmos conhecidos

- Data Encryption Standard (DES).  
- Triple Data Encryption Standard (3DES).  
- Advanced Encryption Standard (AES).  
- International Data Encryption Algorithm (IDEA).  

## Algoritmos de chave assimétrica

Também conhecidos como de chave pública

Par de chaves compatíveis: não existe outra chave que possa ser usada no lugar da original

- Chave privada: mantida em segredo pelo criador do par.  
- Chave pública: distribuída publicamente.  

Toda mensagem cifrada através da chave pública só pode ser decifrado com a chave privada.

    P = DKd(EKe(P)).  
    Kd: chave privada.  
    Ke: chave pública.  

Algoritmos conhecidos

- RSA
- Diffie-Hellman
- Elgamal  

## Comparação de algoritmos

Chave simétrica

- Vantagem: simples e de baixo custo computacional.
- Desvantagens: como enviar a chave única?

Chave assimétrica

- Vantagem: chaves públicas podem ser distribuídas livremente.
- Desvantagem: altamente custoso para processamento.

## Algoritmos de hashing criptográfico

Conhecidos como digestores

- “Digerem” a mensagem e geram um índice hash com ela.

São algoritmos de caminho único

- É computacionalmente impossível recuperar a mensagem.

Funcionamento

- Dada uma mensagem m, de qualquer tamanho, obtém-se o código h, de tamanho fixo para qualquer tamanho de m, através de uma função H.

h = H(m)

Algoritmos conhecidos

- MD5
- SHA

## Autenticação

Permite reconhecer a integridade de uma mensagem ou um usuário (aplicação, host, etc.)

- Dada uma mensagem, pode-se produzir uma cifra que é conferida pelo destinatário.

Também utilizada na criação de chaves de sessão

- Tais chaves são utilizadas para a cifragem de mensagens durante o estabelecimento de um canal seguro.
- Normalmente são descartadas no encerramento do canal.

Três Modelos

- Troca de chaves secretas.
- Uso de um centro de distribuição de chaves.
- Uso de criptografia com chave pública.

## Assinaturas digitais

Assinatura digital é um conteúdo cifrado, transmitido junto com a mensagem para sua conferência

- Capaz de garantir autenticidade (integridade).

Uma forma consiste no uso de chaves assimétricas

- Chave privada é utilizada para cifrar, e a pública para decifrar uma mensagem (modelo usado no PGP).
- Só a chave pública parceira pode decifrar o conteúdo.


P = DKd(EKe(P))  
Kd: chave pública  
Ke: chave privada  

## Assinaturas digitais com chave pública

Sequência

- Alice encaminha uma mensagem m para Bob e, paralelamente, uma versão assinada digitalmente.
- A versão assinada envolve a cifragem de m através da chave privada de Alice e com a chave pública de Bob.
- Bob, ao recebê-la, poderá decifrá-la, primeiramente com sua chave privada, e em seguida, com a chave pública de Alice.
- O resultado então, pode ser comparado com a mensagem originalmente enviada.

![image](https://github.com/user-attachments/assets/05dc1bc1-1c22-466a-b106-347264d76fcf)

## Assinaturas digitais com hashing criptográfico

Dois problemas com a abordagem anterior

- O tamanho da “assinatura” é muito grande.
- O algoritmo utilizado (chave pública) é mais lento.

Aplicação de hashing criptográfico

- Alice encaminha a mensagem m para Bob.
- Paralelamente, processa o cálculo do código hash, através de um message digester.
- O código é cifrado com a chave privada de Alice, e encaminhado a Bob.
- Bob recebe a mensagem m e aplica a mesma função hash, gerando um código.
- Tal código pode então ser comparado ao enviado por Alice, depois que Bob decifrar a assinatura, usando a chave pública de Alice.

![image](https://github.com/user-attachments/assets/3c432258-9690-48b1-a885-0261a6af5845)

## Controle de acesso

Normalmente realizado através de regras explícitas

- Descrevem permissões para usuários, ou grupos de usuários (subjects), para acessos a recursos do sistema (objects).

Monitor de referência

- Provê o acesso/proteção do recurso (objeto), deliberando sobre as regras do controle de acesso.

![image](https://github.com/user-attachments/assets/cb52141a-3e2f-4a70-9ac0-57f221ce5130)


## Controle de acesso – operação

Visa fornecer, ou não, a autorização de acesso a um recurso a determinado usuário (ou entidade)

- Cliente emite requisição de acesso r, que representa um sujeito s, ao servidor que centraliza o controle de acesso.
-  O servidor consulta em sua lista de controle de acesso (ACL – Access Control List) os dados da requisição e do sujeito.
- Se existir regra que permita o acesso, então é autorizado.

![image](https://github.com/user-attachments/assets/3fa9ed92-acad-4ef1-b268-3937a5f01cb3)

## Controle de acesso - tickets

A liberação do acesso pode ser realizada através de tickets

- Um ticket de acesso assinado digitalmente é fornecido ao cliente, que apresentará ao objeto de destino.
- O objeto pode então confirmar a validade daquela autorização com o servidor e atender, ou não, o pedido do cliente.

Tal estratégia reduz bastante a demanda pelo servidor para validação do acesso

![image](https://github.com/user-attachments/assets/f2dc4cdb-1182-4400-b5bb-ae317b9345ec)
