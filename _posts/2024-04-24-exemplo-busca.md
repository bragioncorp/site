---
title: "Exemplos de Exercícios de Busca"
excerpt: "Alguns exemplos de exercícios de Busca para praticar."
categories:
  - IA
tags:
  - IA
  - Inteligência Artificial
  - Busca
  - Exercícios Busca
  - P1

toc: true
---

## Formule os Problemas
Estado inicial (estado do começo do problema).  
Teste de objetivo (o que quero alcançar).  
Função sucessor (função para avançar o estado).  
Função de custo (o que custou mudar de estado).  

### Exercício 1
Você deve colorir um mapa plano utilizando apenas quatro cores de tal modo que não haja duas regiões adjacentes com a mesma cor.  

    Estado inicial: nenhuma região colorida no mapa.
    Teste de objetivo: todas as regiões coloridas e nenhuma região adjacente com a mesma cor.
    Função sucessor: atribuir uma cor a uma região que esteja sem cor.
    Função de custo: número total de atribuições.

### Exercício 2
Um macaco com um metro de altura está em uma sala em que algumas bananas estão suspensas no teto a 2,5 metros de altura. Ajude o macaco a alcançar as bananas. A sala contém dois engradados empilháveis e móveis com um metro de altura cada.  

    Estado inicial: como descrito no enunciado.
    Teste de objetivo: macaco alcançou as bananas.
    Função sucessor: subir no engradado, descer do engradado, mudar o engradado de lugar, andar de um lugar a outro, agarrar bananas
    Função de custo: número total de ações.

### Exercício 3
Considere um programa que emite a seguinte mensagem: “registro de entrada inválido” quando alimentado com um certo arquivo de registros de entrada. Sabendo que cada registro é independente, como descobrir qual registro é inválido?  

    Estado inicial: programa não emite nenhuma mensagem.
    Teste de objetivo: receber a mensagem "registro de entrada inválido".
    Função sucessor: escolher o próximo arquivo para alimentar o sistema.
    Função de custo: número total de escolhas.

### Exercício 4
Três missionários e três canibais estão em um lado de um rio, juntamente com um barco que pode conter uma ou duas pessoas. Sem deixar que um grupo de missionários de um lado fique em número menor que o número de canibais, formule o problema para que eles possam ser levados ao outro lado.

    Estado inicial: como descrito no enunciado.
    Teste de objetivo: transportar os canibais e missionários para o outro lado.
    Função sucessor: escolher o próximo missionário ou canibal para colocar no barco.
    Função de custo: número total de escolhas.

## BFS e DFS
Considere um espaço de estados onde o estado inicial é o número 1 e a função sucessora para o estado n retorna dois estados, com números 2n e 2n+1.
- Desenhe a porção do espaço de estados correspondente aos estados 1 a 15.
- Considere que o estado objetivo seja 11. Liste a ordem em que os nós serão visitados no caso da busca em largura e em profundidade .

![image](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/252a2926-5ae8-400c-a009-6c5c17ff99af)

## Algoritmo
Relembrando:  

>h(n): distância em linha reta (heurística).  
>g(n): distância real (custo acumulado).  

O algoritmo de caminho heurístico é uma busca pela melhor escolha na qual a função objetivo é f(n)=(2-w)g(n)+wh(n).  Responda:
- Para que valores de w esse algoritmo oferece a garantia de ser ótimo?

    Este algoritmo é ótimo quando h(n) é admissível e w=1.  
    A função resultante será: f(n) = g(n)+h(n) que é A*.  

- Qual busca ele executa quando w=0?

    w = 0 faz com que f(n) = 2g(n).  
    Equivale à busca de custo uniforme (a multiplicação por 2 não modifica a ordem em que os nós são expandidos).  

- E quando w = 1?

    w = 1 faz com que f(n)= g(n)+h(n), que equivale à busca A*.  
    É o melhor tipo de busca.  

- E quando w = 2?

    w = 2 faz com que f(n) = 2h(n).  
    Equivale à busca gulosa pela melhor escolha.  