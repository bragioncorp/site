---
title: "Tópicos em computação - grupos e seus temas"
excerpt: "Resumo dos tópicos abordados pelos grupos"
categories:
  - Tópicos em computação
tags:
  - Tópicos em computação
  - Blockchain

toc: true
---

# Blockchain e Criptomoedas

Apresentação Berna e Aranha - 04/09

## Blockchain

- é um sistema de banco de dados avançado
- permite o compartilhamento transparente e seguro de informações de uma rede
- dados armazenados em blocos interligados que formam uma cadeia cronológica imutável (informações não podem ser alteradas nem excluídas)
- tal mecanismo é usado para monitorar transações (pedidos, pagamentos e contas)

## Origem

- origem nos anos 90
- ideia de criar uma rede de blocos protegidos por meio de criptografia, onde ninguém pudesse adulterar
- atualizado com árvores Merkle para aumentar efetividade -> acúmulo de documentos em um só bloco
- a partir de 2008 começou a ganhar popularidade

## Apartir de 2008

Satoshi Nakamoto -> não sabe se é pessoa ou organização de fato
aplicou o conceito digital no bitcoin

## Principais características

### Descentralização

- Distribui o controle e a tomada de decisão por toda a rede
- Reduz a dependencia de autoridades centrais
- Aumenta transparencia e resistencia a falhas

### Imutabilidade

- Transações não pode ser alteradores e excluídas
- Garante integridade e confiabilidade

### Consenso

- Transações só são validades e registradas após a concordância da - Maioria dos participantes da rede
- Assegura legitimidade e concordância coletiva sobre os dados

## Tipos de Blockchain

Publicas -> acesso aberto, qualqer pessoa pode participar e validar transações (bitcoin)

Privadas -> controlada por uma organização com acesso restrito

Híbridas -> combinação do público e privado, quais dados são públicos e quais não

Consórcio -> gerenciadas por organizações que colaboram e compartilham a manutenção da rede

## Impotância

- operação de forma descentralizada
- elimina a necessidade de intermediários confiáveis, reduzindo riscos de fraude e pontos únicos de falha.
- torna transações mais transparentes, seguras e eficientes -> aplicável em diversos setores da economia

Hyperledger Fabric: Framework modular e flexível para soluções empresariais privadas, foco em escalabilidade e segurança.

Ethereum: Plataforma descentralizada popular para a criação de aplicações públicas e contratos inteligentes.

Corda: Projetada para o setor financeiro, facilita transações diretas com altos níveis de privacidade.

Quorum: Variante do Ethereum adaptada para ambientes privados e consórcios empresariais, com melhorias em desempenho e privacidade.

## Aplicações em diferentes setores

### Energia

facilita a comercialização de energia entre pares
permite que proprietários de placas solares vendam excedentes diretamente a consumidores próximos através de plataformas automatizadas e seguras

### Financeiro

aprimorar processos de pagamentos e liquidações, tornando-os mais rápidos e confiáveis
otimização de transações e redução de processos manuais complexos

### Mídia e entretenimento

gerencia e protege direitos autorais, assegurando competência justa dos artistas
simplifica processo de verificação e transferência de direitos através de registros imutáveis

### Varejo

monitoramento e autenticação de produtos ao longa da cadeira de suprimentos
autentiicdade das mercadorias e aumento da confiança dos consumidores por meio de rastreabilidade transparente

## Conclusão

blockchain representa uma revolução na forma como transações e dados são gerenciados
oferecem segurança, transparência e eficiência
suas diversas aplicações mostram o seu potencial transformador
impulsiona inovação e confiança em processos digitais globalmente

# Bioinformática

Apresentação Matheus Gomes e Ivo - 11/09

## O que é

Campo interdisciplinar que combina biologia, ciência da computação e matemática para analisar e interpretar dados biológicos.

Sua história começa na segunda metada do século XX, impulsionada pelo avanço das tecnologias computacionais e pela necessidade de gerenciar grandes volumes de dados biológicos.

## Breve história

Pioneiros como Margare Dayhoff (1950 - 1960) começaram a aplicar métodos computacionais para comparar sequências para comparar sequências de proteínas.

Com o avanço dos computadores e dos métodos de sequenciamento de DNA (1970 - 1980), a bioinformática focou na análise de sequências biológicas.

Projeto Genoma Humano (1990) impulsionou o campo ao gerar grandes volumes de dados genômicos, necessitando de novas ferramentas de análise.

Com a chegada das tecnologias de sequecimaneto da nova geração nos anos 2000 a bioinformática se expandiu para outras "ômicas" como transcriptômica e proteômica, sendo hoje essencial para a biologia, medicina personalizada e desenvolvimento de novas terapias.

> marcos importantes: Projeto Genoma Humano, desenvolvimento de algoritmos para comparação de sequências.

## Aplicações

### Genômica e medicina personalizada

Análise do genoma individual para identificar predisposições genéticas a doenças e personalizar tratamentos.

Ex: Testes genéticos para prever resposta a medicamentos (farmacogenômica), tratamentos direcionados para câncer com base em mutações específicas.

### Agricultura e biotecnologia

Aplicação de técnicas de bioinformática para melhoramento genético de plantas e animais.

Ex: Identificação de genes para resistência a doenças em plantas e desenvolvimento de culturas geneticamente modificadas.

Benefícios: Aumento da produtividade agrícola, resistência a pragas e condições climáticas adversas.

### Descoberta e desenvolvimento de medicamentos:

uso de simulações e modelagem molecular para identificar e otimizar compostos candidatos a medicamentos.

Ex: Modelagem de proteínas para encontrar sítios de ligação de drogas e prever interações moleculares.

benefícios: Aceleração do desenvolvimento de medicamentos, redução de custos com ensaios laboratoriais.

## NCBI

O NCBI (National Center for Biotechnology Information) e é um dos principais repositórios globais de informações biológicas e genômicas

Fundado em 1988, o NCBI fornece acesso a uma vasta coleção de bancos de dados, como o GenBank para sequências de DNA e RNA, e o PubMed para literatura científica.

Oferece o BLAST (Basic Local Alignment Search Tool) que permite a comparação de sequências biológicas para identificar similaridades funcionais e evolutivas.

NCBI é essencial para pesquisadores e profissionais da área, pois facilita o acesso a dados genômicos e ferramentas de análise, impulsionando descobertas científicas, avanços em biotecnologia, e o desenvolvimento de novas terapias na medicina personalizada.

## Ferramentas e tecnologias

### Específicas

BLAST: Comparação de sequências para encontrar similaridades (identificação de genes, análise de homologia).
ClustalW: Alinhamento múltiplo de sequências (estudos filogenéticos, análise evolutiva).
Bowtie: Alinhamento rápido de sequências de DNA (análise de dados de sequenciamento, mapeamento de reads).

### Programação

Conjuntos de ferramentas de software desenvolvidas em diferentes linguagens de programação (Python, Java, Perl) para manipulação e análise de dados biológicos.
Servem para automação de processos bioinformáticos, manipulação de sequências de DNA, RNA, e proteínas, acesso a bancos de dados biológicos...

## Desafios atuais na bioinformática

Volume crescente de dados biológicos, exigindo infraestrutura avançada para armazenamento e análise.

Integração de dados heterogêneos e a falta de interoperabilidade entre ferramentas dificultam a análise e interpretação precisas.

Necessidade crítica de garantir a segurança e privacidade de dados genéticos, especialmente em contextos colaborativos.

## Futuro

Tedências que incluem o uso crescente de inteligênica artificiall e machine learning para análise de big data, impulsionando a medicina personalizada com tratamentos individualizados baseados em perfis genômicos.

Tecnologias de sequenciamento de terceira geração, como o sequeciameto por nanopore, oferecem leituras longas e em tempo real, com potencial de reduzir custps e expandir o uso clínico.

Dispositivos portátiveis estão possibilitando análises genômicas em campo, ampliando as aplicações da bioinformática em áreas como agricultura, conservação e saúde pública.

# Privacidade de Dados

Apresentação Leo Basso e João Vitor - 18/09

## O que é?

### Definição de privacidade de dados pessoais:

Privacidade de dados pessoais refere-se à proteção das informações que podem identificar diretamente ou indiretamente uma pessoa. Isso envolve o controle sobre como os dados são coletados, armazenados, compartilhados e usados, garantindo que indivíduos mantenham sua autonomia e confidencialidade no ambiente digital.

### Por que a privacidade de dados é importante na era digital?

Na era digital, grandes volumes de dados são coletados por empresas e governos, e a falta de proteção adequada pode levar a fraudes, roubos de identidade e invasões de privacidade. A proteção desses dados é essencial para preservar direitos individuais e evitar o uso indevido de informações pessoais.

## Principais ameaças à privacidade de dados.

### Ciberataques: phishing, malware, ransomware:

Ciberataques como phishing, malware e ransomware visam roubar ou comprometer dados pessoais.  
Phishing envolve enganar usuários para fornecerem informações sensíveis, enquanto malware infecta dispositivos para roubar dados.  
Ransomware criptografa dados e exige pagamento para liberá-los, causando grandes prejuízos a indivíduos e empresas.

### Vazamentos de dados: causas e impactos:

Vazamentos de dados ocorrem quando informações sensíveis são expostas devido a falhas de segurança, ataques cibernéticos ou erros humanos. Os impactos incluem perdas financeiras, danos à reputação e riscos de fraude ou roubo de identidade, afetando tanto usuários quanto organizações responsáveis pela proteção dos dados.

### Coleta indevida de dados por empresas: rastreamento online, uso de cookies.

Empresas muitas vezes coletam dados pessoais indevidamente através de rastreamento online e cookies sem o consentimento claro dos usuários.  
Essas práticas podem violar a privacidade ao monitorar hábitos de navegação, comportamento de compras e localização, usando essas informações para publicidade direcionada ou outras finalidades não autorizadas.

## Técnicas para proteção de dados pessoais.

### Criptografia: como funciona e sua importância:

Criptografia é o processo de codificação de dados, tornando-os ilegíveis para qualquer pessoa sem a chave de decriptação. Ela protege informações confidenciais contra acessos não autorizados, sendo essencial para garantir a segurança em comunicações digitais, transações financeiras e armazenamento de dados pessoais.

### Anonimização e Pseudonimização: diferenças e aplicações

Anonimização remove qualquer identificação dos dados, impossibilitando a reidentificação de um indivíduo.  
Pseudonimização substitui informações identificáveis por pseudônimos, permitindo a reversão sob condições específicas.  
Ambas são usadas para proteger dados em conformidade com regulamentos, mas a anonimização oferece maior segurança.

### Autenticação Multifator (MFA)

Autenticação Multifator (MFA) exige que o usuário forneça dois ou mais elementos de verificação (senha, biometria, token) antes de acessar uma conta ou sistema.  
Isso dificulta acessos não autorizados, mesmo que uma das credenciais seja comprometida, aumentando significativamente a segurança dos dados.

### Backup de dados: proteção contra perda e ataques de ransomware

O backup de dados é a prática de criar cópias redundantes de informações importantes, armazenando-as em locais seguros.  
Essa medida protege contra perda de dados devido a falhas no sistema, erros humanos ou ataques de ransomware, permitindo que os dados sejam restaurados em caso de incidentes.

## Regulamentos de proteção de dados

### GDPR (Regulamento Geral de Proteção de Dados - Europa): princípios e aplicação.

O GDPR é a lei europeia que regula o tratamento de dados pessoais, garantindo a privacidade e proteção dos indivíduos. Seus princípios incluem transparência, limitação de propósito, minimização de dados e segurança. Ele se aplica a todas as empresas que processam dados de cidadãos da UE, impondo pesadas multas em caso de descumprimento.

### LGPD (Lei Geral de Proteção de Dados - Brasil): principais pontos e obrigações

A LGPD é a legislação brasileira que regula o uso de dados pessoais, inspirada no GDPR. Ela exige o consentimento explícito dos titulares para o processamento de seus dados, além de assegurar direitos como acesso, correção e exclusão de informações. As empresas precisam implementar medidas de segurança e nomear um encarregado de proteção de dados (DPO).

### Outros regulamentos globais (CCPA, HIPAA, etc.):
Outros regulamentos importantes incluem o CCPA (California Consumer Privacy Act), que dá aos consumidores da Califórnia mais controle sobre seus dados, e a HIPAA (Health Insurance Portability and Accountability Act), que protege informações de saúde nos EUA. Esses regulamentos refletem a crescente preocupação global com a privacidade de dados em diferentes setores.

## Como as empresas  se adaptam aos regulamentos?

### Compliance (Conformidade): como as empresas garantem que estão em conformidade com as leis.

Compliance envolve a adoção de práticas e políticas que asseguram que as empresas sigam as leis de proteção de dados, como LGPD e GDPR. Isso inclui a criação de políticas internas, treinamento de funcionários, nomeação de um DPO, e implementação de medidas técnicas e organizacionais para garantir a segurança dos dados.

### Processos internos e auditorias: implementação de políticas de privacidade.

Empresas desenvolvem processos internos para garantir a privacidade, como revisão de contratos, controle de acesso a dados e monitoramento do fluxo de informações. Auditorias periódicas avaliam a eficácia das medidas adotadas e verificam se estão alinhadas às exigências legais, corrigindo eventuais falhas.

### Multas e penalidades: consequências do não cumprimento.

O não cumprimento das leis de proteção de dados pode resultar em multas elevadas, como até 4% do faturamento anual global no caso do GDPR, ou até R$ 50 milhões por infração com a LGPD. Além das penalidades financeiras, há danos à reputação e perda de confiança dos clientes, o que pode impactar significativamente os negócios.

## Exemplos recentes de violação de dados.

### Caso Facebook-Cambridge Analytica

Envolveu a coleta indevida de dados de 87 milhões de usuários do Facebook sem consentimento, usada para influenciar campanhas políticas, incluindo as eleições presidenciais dos EUA em 2016. A Cambridge Analytica utilizou informações pessoais para criar perfis psicológicos e direcionar propaganda política. O escândalo gerou grandes repercussões, resultando em investigações globais e multa bilionária ao Facebook, além de levantar questões sobre privacidade e manipulação de dados online.

### Caso Yahoo (2013-2014)

Entre 2013 e 2014, o Yahoo sofreu o maior vazamento de dados da história, com mais de 3 bilhões de contas afetadas. Informações como e-mails, datas de nascimento e senhas criptografadas foram expostas. A falha de segurança, revelada apenas em 2016, impactou gravemente a confiança dos usuários e contribuiu para a venda da empresa à Verizon por um valor reduzido.

### Caso Uber (2016)

Em 2016, a Uber sofreu uma violação que expôs dados de 57 milhões de motoristas e passageiros. A empresa, em vez de notificar as autoridades, pagou US$ 100 mil aos hackers para encobrir o incidente. Quando o caso veio a público em 2017, a Uber enfrentou uma grave crise de confiança e multas por falha em relatar a violação de maneira adequada.

## Desafios atuais e futuros da proteção de dados

### Tecnologias emergentes: IA, IoT e seus impactos na privacidade.

A Inteligência Artificial (IA) e a Internet das Coisas (IoT) estão transformando a coleta e análise de dados, permitindo automação e conectividade em larga escala. No entanto, essas tecnologias aumentam os riscos à privacidade, já que mais dados pessoais são processados em tempo real, muitas vezes sem controle adequado ou consentimento explícito dos usuários.

### Dificuldade em equilibrar inovação e proteção de dados.

O rápido avanço tecnológico desafia a capacidade de equilibrar inovação com a proteção de dados pessoais. Empresas buscam explorar ao máximo as informações dos usuários para desenvolver produtos e serviços, mas precisam garantir conformidade com as leis de privacidade, o que pode limitar o uso de certos dados e criar obstáculos regulatórios.

### Tendências futuras: novas regulamentações, aumento da conscientização.

Espera-se que novas regulamentações globais sejam implementadas para acompanhar o desenvolvimento tecnológico, especialmente em áreas como IA e IoT. Além disso, a conscientização dos usuários sobre a importância da privacidade tende a crescer, impulsionando uma demanda maior por transparência e controle sobre seus dados pessoais.

## Conclusão

Resumo

Nesta apresentação, exploramos a privacidade de dados pessoais, destacando técnicas de proteção como criptografia e pseudonimização, e discutimos regulamentos como GDPR e LGPD. Analisamos os impactos de violações de dados e as medidas necessárias para garantir a conformidade, incluindo a importância do DPO e a implementação de políticas internas robustas.

A privacidade de dados é crucial para proteger direitos individuais e evitar abusos. Conformidade com regulamentações como GDPR e LGPD não apenas evita multas e danos à reputação, mas também constrói confiança com os clientes. A adoção de práticas de proteção de dados é essencial para garantir segurança e respeito às informações pessoais em um mundo cada vez mais digital.