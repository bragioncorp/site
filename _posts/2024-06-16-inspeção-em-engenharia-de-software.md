---
title: "Inspeção em Engenharia de Software"
excerpt: "Resumo sobre inspeção em Engenharia de Software."
categories:
  - Engenharia de Software
tags:
  - Engenharia de Software
  - Inspeção
  - Inspeção de Software
  - Revisão dos Artefatos produzidos
  - Benefícios das Inpeções
  - Práticas Recomendadas

toc: true
---

Na engenharia de software é necessário considerar esforço, produtividade, tempo e custo.

- Essas variáveis são afetadas negativamente quando artefatos defeituosos são produzidos, devido ao retrabalho para corrigir o defeito.
- O custo do retrabalho para correção aumenta de acordo com o desenvolvimento do projeto.
- Iniciativas devem ser realizadas para encontrar e corrigir defeitos tão logo sejam introduzidos.

## Revisão dos artefatos produzidos

Abordagem que tem se mostrado eficiente e de baixo custo para encontrar defeitos, reduzir o retrabalho e melhorar a qualidade.

## Inspeção de software

Processo de detecção rigoroso e bem definido para todos os artefatos de software.

## Terminologia padrão

### Erro

Ação equivocada por um indivíduo, imprudência ou inabilidade no método.

### Defeito

Manisfestação concreta de um erro em um artefato.

Erro pode resultar em diversos defeitos.

### Falha

Comportamento operacional do software diferente do esperado pelo usuário.

## Consequências da falta de Inspeções de Software

O esforço gasto com retrabalho varia em média entre 40% ou 50% do total do desenvolvimento de um projeto.

## Padrão IEEE 830 - recomenda práticas para análise de requisitos

Podem ser consideradas em qualquer artefato.

### Omissão

Algum requisito que não foi incluído,  
não está bem definido a resposta do software para as entrada de dados,  
faltam seções na especificação do requisito,  
faltam referências ou imagens,  
ou falta definição de termos.

### Ambiguidade

Um requisito tem várias interpretações ou vários significados.

### Inconsistência

Dois ou mais requisitos são conflitantes.

### Fato Incorreto

Um requisito descreve um fato que não é verdadeiro.

### Informação estranha

Informações fornecidas no requisito não são necessárias ou mesmo usadas.

### Outros

Inclusão de um requisito numa seção errada do documento.

## Benefícios das inspeções

- Detecção de defeitos nas fases iniciais do processo de desenvolvimento de software, facilitando a correção destes defeitos com menor esforço e custo.
- O esforço com retrabalho é reduzido em média para 10% a 20% do esforço total de desenvolvimento.
- Essa redução no retrabalho pode implicar em melhorias significativas para a produtividade de software.

Esforço: reduzido em 44%.  
Produtividade: aumentada em 30% a 50%.  
Tempo: reduzido em 10% a 30%.  
Custo: reduzido em 39%.

## Benefícios secundários das inspeções

### Aprendizado

Inspetores experientes podem tentar detectar padrões de como os defeitos ocorrem e definir diretrizes que ajudem na detecção destes (bons padrões) para serem adotados como melhores práticas da organização.

### Integração

Saber onde e quando os defeitos ocorrem pode ajudar a estabelecer planos de contingência que evitem a sua ocorrência.

### Produtos Inteligíveis

Artefatos passarão a produzir artefatos de uma forma que sua compreensão seja facilitada, trazendo benefícios no desenvolvimento e manutenção.

### Ajustes no Processo

Evitam a ocorrência de defeitos repetidos em outros projetos.

## As seis atividades principais do processo de Inspeção

### Planejamento

O moderador define o contexto da inspeção (descrição da inspeção, técnica a ser utilizada na detecção de defeitos, documento a ser inspecionado, autor do documento, entre outros), seleciona os inspetores e distribui o material a ser inspecionado.

### Apresentação

Os autores dos artefatos a serem inspecionados apresentam as características destes. Esta fase pode ser omitida se os inspetores possuem conhecimento sobre o projeto e os artefatos que devem ser inspecionados.

### Preparação

Inspetores estudam os artefatos individualmente e fazem anotações sobre estes produzindo uma lista de discrepâncias.

### Reunião

Envolve o moderador, os inspetores e os autores do documento. Discrepâncias são discutidas, e classificadas como defeito ou falso positivos e a decisão final sobre a classificação é do moderador.

### Retrabalho

O autor corrige os defeitos encontrados pelos inspetores e confirmados pelo moderador.

### Continuação

Material corrigido pelos autores é repassado para o moderador, que faz uma análise da inspeção como um todo e reavalia a qualidade do artefato inspecionado.

## Atividades Sequenciais

- Processo alternativo que mantém a estrutura sistemática e os aspectos colaborativos do processo tradicional.
- Substitui as atividades de preparação e de reunião do processo tradicional por três novas atividades sequenciais.

### Detecção de defeitos

Cada um dos inspetores selecionados pelo moderador realizará uma atividade de detecção de defeitos para produzir uma lista de discrepâncias.

### Coleção de defeitos

O moderador agrupa as listas de discrepâncias dos inspetores e elimina as repetições.

### Discriminação de defeitos

O moderador, o autor do documento e os inspetores discutem as discrepâncias e algumas serão classificadas como falso positivo e outras como defeito. Os falsos positivos serão descartado e os defeitos serão registrados e passados ao autor para correção.