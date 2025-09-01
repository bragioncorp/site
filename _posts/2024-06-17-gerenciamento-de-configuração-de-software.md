---
title: "Gerenciamento de Configuração de Software"
excerpt: "Gerenciamento de Configuração de Software em Engenharia de Software."
categories:
  - Engenharia de Software
tags:
  - Engenharia de Software
  - Gerenciamento de Configuração de Software
  - Gerenciamento de Configuração
  - Gerência de Configuração
  - GC
  - Item de Configuração
  - Baseline
  - Repositório
  - Lock
  - Check-Out
  - Check-In
  - Build
  - Release
  - Tags
  - Branch
  - Merge
  - Controle de Mudanças
  - Gerência de Mudanças
  - Ciclo de Vida de um Artefato
  - Artefato Draft
  - Artefato Aceito
  - Artefato em Manutenção
  - CCB
  - Análise de Impacto

toc: true
---

## Objetivo

Compreender a importância do uso de mecanismos de gerência de configuração e de mudança, seus métodos, processos e ferramentas.

## Problemas

Problemas em desenvolver versões diferentes do projeto.

- Falha de comunicação em equipes.
- Vocabulários incompatíveis.
- Culturas de desenvolvimento diferentes.
- Distância geográfica.
- Dificuldade de expressão.

## Consequências?

Os sistemas produzidos não atendem aos requisitos.  
Força de trabalho é desperdiçada.

## Problema de Dados Compartilhados

> Ex: dev A modifica um componente, mas o dev B não tem a menor ideia sobre isso.
> 

### Solução Simplista:

Cada desenvolvedor trabalha em uma cópia “local” do componente.  
Resolve o problema dos dados compartilhados, mas cria um novo problema.

## Problema da Manutenção Múltipla

Ocorre quando cada desenvolvedor trabalha com uma cópia “local” do que seria o mesmo componente.

Dificuldade para saber:

- Que funcionalidades foram implementadas em quais versões do componente.
- Que defeitos foram corrigidos.

Evitado através de uma biblioteca central de componentes compartilhados, mas cria um novo problema.

## Problemas de Atualização Simultânea

> Ex: dev A corrige um defeito, o dev B não soube da correção e também corrige o defeito, desperdiçando o trabalho do dev A.
> 

### Como resolver?

O problema da atualização simultânea não pode ser resolvido simplesmente copiando componentes compartilhados para uma biblioteca central.  
Algum mecanismo de controle é necessário para gerenciar a entrada e saída dos componentes.

## Gerência de Configuração (GC)

É o processo de identificar, organizar e controlar modificações ao software sendo construído.  
A ideia é maximizar a produtividade minimizando os enganos.

## Objetivos da GC

Definir o ambiente de desenvolvimento.  
Definir políticas para controle de versões, garantindo a consistência dos artefatos produzidos.  
Definir procedimentos para solicitações de mudanças.  
Administrar o ambiente e auditar mudanças.  
Facilitar a integração das partes do sistema.

## Benefícios

Aumento de produtividade no desenvolvimento.  
Menor custo.  
Redução de defeitos.  
Maior rapidez na identificação e correção.

# Conceitos Básicos

## Configuração

Um projeto de desenvolvimento produz:

- Programas (código fonte, programas executáveis, bibliotecas de componentes).
- Documentação (manuais do usuário, documento de requisitos, modelo de análise e projeto).
- Dados (dados de teste e do projeto).

Chamados coletivamente de configuração do software.

## Item de Configuração

Conjunto de itens de hardware e/ou software vistos como uma **entidade única para fins de gerência de configuração**.  
Um item de configuração está sujeito a mudanças e essas devem obedecer às políticas estabelecidas.  
Um item de configuração é estabelecido para cada pedaço de software que pode ser projetado, implementado e testado de forma independente.

### Baseline

Especificação ou produto que foi **formalmente revisado e aceito**.  
A configuração do software em um ponto discreto no tempo.  
Só pode ser modificado através de procedimentos formais

### Razões para criar um baseline

Reprodutibilidade: reproduzir versão anterior do sistema.  
Rastreabilidade: relação predecessor-sucessor entre artefatos do projeto.  
Geração de relatórios: comparação com baselines passados.  
Baselines são considerados marcos no processo de desenvolvimento:

- Funcional : requisitos
- De Produto : releases, iterações

### Repositório

Local (físico e lógico) onde os itens de um sistema são guardados.  
Pode conter diversas versões do sistema.  
Utiliza mecanismos de controle de acesso.

### Lock

Resolve a atualização simultânea.  
Garante que apenas um usuário (detentor do lock) altere o arquivo.  
Problema: “serializa” o trabalho dos desenvolvedores.

### Check-Out

Recupera a última versão de um item de configuração guardada no repositório.  
- Escrita: verifica se ninguém detém o **LOCK**, obtém o **LOCK**, cria uma cópia para edição.  
- Leitura: verifica que alguém já detém o **LOCK**, cria uma cópia apenas para leitura.

### Check-In

Ação de inserir/atualizar um item de configuração no repositório.  
- Verifica o **LOCK** do item de configuração, caso o mesmo já exista.  
- Verifica e incrementa a versão do item.  
- Registra informações das mudanças (autor, data, hora, comentários).  
- Inclui/atualiza o item.

### Build

Versão ainda incompleta do sistema em desenvolvimento, mas **com certa estabilidade**.  
Apresenta limitações conhecidas.  
Espaço para integração de funcionalidades.  
Inclui código fonte, documentação, arquivos de configuração, base de dados.

### Problemas na geração das builds:

Fazer os builds do sistema manualmente é muito demorado.  
Pode ser difícil saber qual a versão “correta” de um arquivo.  
Os pedaços do sistema podem estar em diversos locais diferentes.  
Alguns arquivos podem ser esquecidos.  

> Integrar as partes de um sistema é uma tarefa trabalhosa e sujeita a erros.
> 

> Quanto maior o sistema, mais difícil.
>

### Release

Identificação e empacotamento de artefatos entregues ao cliente (interno ou externo) ou ao mercado.  
Implica no estabelecimento de um **novo baseline**.  
Produto de software supostamente sem erros.

### Tipos de Release

internos: controle de qualidade, acompanhamento do projeto, controle de riscos, aceitação, aquisição de conhecimento através da coleta de feedbacks, desenho da estratégia.  
externos: implantado e utilizado pelo cliente.

### Tags

Rótulos que são associados a conjuntos de arquivos.  
Uma tag referencia um ou mais arquivos em um ou mais diretórios

Denomina projeto rotulando todos os arquivos associados ao projeto.  
Denomina uma versão do projeto (um build ou release) rotulando todos os arquivos associados ao build ou release.

### Branch

Criação de um fluxo alternativo para a atualização de versão.  
Recurso muito **poderoso**.  
Devem existir regras bem definidas para a criação de branches.  
**Uso de lock inviabiliza a criação de branches**.  
Branches normalmente se originam de correções em versões anteriores.

### Merge
Unificação de diferentes versões de um mesmo item de configuração.  
integração dos itens de configuração de um branch com os itens de configuração do fluxo principal.  
Check-out atualizando a área local.  
Algumas ferramentas fornecem um mecanismo automático para realização de merges.  
Mesmo com o uso de ferramentas, em vários casos há necessidade de intervenção humana.

# Controle de Mudanças

## Contexto

Desenvolvimento iterativo/incremental.  
Novos conjuntos de requisitos, detalhados a cada iteração.  
Mudanças em estratégias de negócio motivadas pelas mais diversas fontes: mercado, cultura, leis, etc.

## Problemas

Controle do escopo do projeto.
- Modificações podem ampliar o leque de funcionalidades e aumentar significativamente o custo do projeto.

Controle de consistência dos artefatos.
- Uma mudança aparentemente localizada pode causar muito mais impacto do que o previsto.
- Degradação da qualidade do software.
- Retrabalho.

## O que é Gerência de Mudanças (GM)?

É o processo de avaliar, coordenar e decidir sobre a realização de mudanças propostas a Itens de Configuração (ICs).  
Mudanças aprovadas são implementadas nos itens de configuração e nos dados e documentos relacionados.  

## Objetivos da GM

Garante que os artefatos do sistema alcancem e mantenham uma estrutura definida através do seu ciclo de vida.  
Define procedimentos e documentação necessários para realizar modificações a ICs.  
Provê os mecanismos necessários para conduzir mudanças de uma maneira controlada.

### Benefícios

Controle sobre o escopo do projeto.  
Mais produtividade.  
Mais qualidade.

# Ciclo de vida de um artefato

![image](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/968a9fee-a7ed-4482-b9d1-cbf7e254c76c)

## Artefato Draft

Mudanças frequentes e rápidas.  
Demanda por agilidade.  
Controle formal dificulta a criação do artefato.

## Artefato Aceito

Artefato seguiu um processo de revisão, testes e aceitação.  
Inserido dentro do processo de controle de mudanças, **tornando-se de fato Item de Configuração**.  
Mudanças via solicitação formal.  
Presença do grupo gestor de mudanças (CCB) para avaliar e priorizar mudanças.

## Artefato em Manutenção

Após a entrega de uma versão do produto, os artefatos passam para a fase de manutenção.  
Controle de mudanças permanece formal para os artefatos de um **baseline**.  
Novos artefatos podem ser desenvolvidos usando o mesmo modelo de ciclo de vida.  
Sistema pode ser descontinuado ou removido do ambiente de produção.

# CCB

## Responsabilidade

Analisar as solicitações de mudança.  
Controlar o escopo do projeto.  
Reuniões com frequência adequada ao ritmo das solicitações de mudança.  
Envolver stakeholders no processo de priorização no processo de decisão.  
Balanço entre o nível de controle desejado e overhead suportado.

## Características

Composição multidisciplinar.  
Profissionais com grande capacidade de comunicação e negociação.

# Análise de Impacto

Devem ser comunicadas aos stakeholders envolvidos.  
Análises de custo x benefício produzidas pelos stakeholders.  
Priorização de mudanças.  
Mudança pode ser rejeitada se o CCB perceber que o custo será mais caro que o benefício percebido.  
Por questões de eficiência, algumas solicitações de mudança podem ser agrupadas por tema, subsistema ou área de negócio.