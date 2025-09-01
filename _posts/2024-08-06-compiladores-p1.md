---
title: "Compiladores - Resumão para P1"
excerpt: "Resumo Compiladores"
categories:
  - Compiladores
tags:
  - Compiladores
  - Resumo
  - Teoria
  - Análise Léxica
  - Análise Sintática
  - Análise semântica
  - Gerador de código

toc: true
---

# Aula I

## Compilar

Traduzir algo escrito em uma determinada linguagem para uma linguagem de máquina.

Traduz um código fonte (alto nível) para um código objeto binário (baixo nível).

Código fonte -> compilador -> código executável

## História

no inicio programas eram escritos em ling de maq

o primeiro compilador foi criado por Grace Hooper em 1952, A-0 System (Univac I)

compilador completo em 1957, FORTAN - John Backus

## Componentes

- Análise léxica
- Análise sintática
- Análise semântica
- Geração e otimização de código

### Analise léxica

Vai executar os autômatos.

Identificar os elementos do textos, caractere por caractere.

Verificar se a palavra é reservada, constante, variável.

Ignora comentários.

### Analise sintática

Identifica as construções válidas da linguagem com base nos elementos léxicos.

### Analise semântica

Garante que as construções identificadas façam sentido de acordo com as regras da linguagem.

Verifica se as variáveis usadas foram devidamente declaradas

### Gerador de código

Criação de código de baixo nível que reflete os comandos do código fonte.

Otimização dos comandos gerados para uma determinada arquitetura.

## Exemplo

soma := soma + 35

### Análise léxica

(valor)	(classe)

SOMA	identificador

:=		comando de atribuição

SOMA	identificador

+		operador numérico de adição

35		constante numérica inteira

### Análise sintática

Árvore de execução (desenho).

Caso a análise léxica esteja certa, constrói a árvore e código está certo.

Distribui as expressões, sequencias e operações

Em linguagens formais e autômatos → processo de derivação na linguagem → procurava derivar.

Criava a árvore de derivação → aqui é árvore sintática.

Linguagens formais não seguiam nenhum algoritmo específico → tentava e erro.

![analisador sintatioc](https://github.com/user-attachments/assets/ba88ab9b-9808-48f5-b784-49ade1dd71fc)

### Análise semântica

SOMA foi declarada?

SOMA é variável?

Qual o escopo de SOMA?

Qual o tipo de SOMA?

Coloca informações adicionais na árvore

### Geração de código

Movimentação de registradores

Código dentro do processador (assembly).

```nasm
MOV AX, [soma]
ADD AX, 35
MOV [soma], AX
```

## Componentes em detalhes

![componentes em detalhes](https://github.com/user-attachments/assets/2b13cdb6-d29f-4d6f-99b8-3801f90ef3d8)

## Compiladores vs Interpretadores

Existência das três analises (léxica, sintática e semântica).

Compilador faz trabalho rápido.

Interpretadores geram código objeto durante a execução.

Interpretadores são mais lentos, porem alterações no código são mais rápidas de serem realizadas.

## Bytecode

Presente no Java.

Ao invés de gerar comandos em linguagens de maquina, os comandos são armazenados na forma de códigos binários.

Este código será então interpretado por uma maquina virtual.

Compila até uma parte, depois manda para a máquina virtual.

Bom para rodar em arquitetura diferentes (um código Java feito no Linux pode rodar no Linux, Windows e Mac sem problemas).

# Alula 2

## O que é gramática?
Gramática é uma ferramenta para descrever uma linguagem.  
É a base do analisador léxico e sintático.

## Onde autômatos finitos são utilizados?
Autômatos finitos são utilizados na análise lexicográfica para reconhecimento dos programas e na definição de suas estrutras.

## O que é um compilador?
É um tradutor entre duas linguagens (L1 e L2) de programação.  
Neste caso L1 representa o código fonte e L2 o código de máquina.

## Relembrando
Alfabeto: conjunto finito não vazio de símbolos.  
Palavra: sequência finita de símbolos do alfabeto.  
Comprimento da palavra: número de símbolos que compõem a palavra.  
Concatenação ou produto de palavras.  

Uma linguagem sobre um alfabeto Σ é um subconjunto de Σ*.  

## Qual é a regra geral da gramática?
Gramática G=(V,T,P,S), onde:  
– V: conjunto de símbolos não terminais  
– T: conjunto de símbolos disjuntos de V  
– P: conjunto de regras de produção  
– S: elemento de V denominado inicial  

## Exemplo 1

![image](https://github.com/user-attachments/assets/95ab7a54-aeb1-4b40-a929-4c4f5dfa21ba)

![image](https://github.com/user-attachments/assets/d49bee0b-8b81-4ee7-b602-484953de031a)


## Exemplo 2

Obs: fere regra de produção - símbolos não terminais não podem estar nos dois lados (EOE).

![image](https://github.com/user-attachments/assets/7f75468b-c8aa-4685-93b3-88c0d093270e)

![image](https://github.com/user-attachments/assets/657c1152-311b-471d-a0b3-53c9d12a137d)

## Detecção de erros

### Dinâmicos
São erros originados em tempo de execução
Ex: input não esperado do usuárui

### Estáticos
São erros encontrados durante a compilação
- identificadores ma contruidos (analise lexica).  
	Verifica se reconhece os elementos.  
  Ex: na seguiu as regras de variaveis

- Desrespeito a gramatica - "syntaxa error" (analise sintatica).  
 - Desrespeita a política de tipos, visibilidade de identificadores, passagem de parâmetros, etc (análisesemântica).  

![image](https://github.com/user-attachments/assets/2e467e89-2b16-4cbb-8b51-38c660fd7ecb)

## Qual a função da análise léxica?
Sua função é ler o arquivo fonte e "etiquetar" os elementos significativos.  
Estes elementos significativos são chamados de **tokens**

## O que são tokens?
Tokens são os significados dos padrões de caracteres em um código fonte.

O processo de varredura é um caso especial de casamento de padrões.  
Métodos utilizados: Expressão regular (ER) e autômatos finitos.  
A velocidade do processamento é um ponto crítico.  

## O que é lexema?
Lexema é a sequência de caracteres na fonte que se associa a um padrão e então a um token - instância do token.  

## Simplificando
Lexema -> variavel / operação encontrado no codigo (if, sum, ...)  
Token -> como é representada |(numero, literal, ...)

![image](https://github.com/user-attachments/assets/b067dee1-2f27-4dbb-bab7-e2976704ada1)

A palavra léxico faz referencia ao conjunto teoricamente infinito de todas as palavras já realizadas e potenciais de uma língua  
Em linguagem de programação, palavras são objetos como nomes de variáveis, números, keywords.  
Estas palavras são chamadas de tokens.  

![image](https://github.com/user-attachments/assets/394ead41-865c-4001-aea5-862ee95775e4)

Entenda VALOR como Lexema e CLASSE como Token.

Input: letras individuais das palavras.  
Output: strings divididas em tokens.  
Descarta espaços em branco (espaços, quebra de linha e etc) e comentários.  

## Qual o objetivo da análise léxica?
Facilitar o trabalho do analisador sintático.

## Por que separar o analisador léxico do analisador sintático?
Pois é mais eficiente, modular e tradicional.

## O que faz um gerador léxico?
Transforma especificações de tokens e espaços em branco (em linguagem humana compreensível) em programas eficientes.  

Especificações léxicas são geralmente escritas usando expressões regulares.  
ER: notação algébrica para descrever um conjunto de caracteres.  
Assim, os gerados léxicos são descritos como autômatos finitos.  

## Análise léxica - ER

![image](https://github.com/user-attachments/assets/90d05d27-7126-4c17-8b14-cac72591d56b)

![image](https://github.com/user-attachments/assets/cbfaed32-8d95-4e22-bff3-d69ea0ccae50)

## Estrutura léxica - MiniJava

![image](https://github.com/user-attachments/assets/b92c03a4-6cf2-469c-8871-0ac7279a345f)

## Análise léxica - ER (continuação)

![image](https://github.com/user-attachments/assets/70b6b57a-be8a-4681-857e-632f9896fe68)

## Exercício 1

![image](https://github.com/user-attachments/assets/9a80776c-8ba7-4476-a870-a7924c3c18e1)

## Respostas  
a)  0*  
    42  

b)  0∗  
    ([0−9] |  
    [1−3][0−9] |  
    4[0−1] |  
    4[3−9] |  
    [5−9][0−9] |  
    [1−9][0−9][0−9]+)  

c)  0∗
    (4[3−9] |  
    [5−9][0−9] |  
    [1−9][0−9][0−9]+)  

## Qual é o melhor autômato para reconhecer as palavras?
É p autômato finito deterministico com o minimo de estados.  

## Vamos estudar 3 etapas
- ER para Autômato Finito Não Deterministico (AFN).
- Autômato Finito Não Deterministico (AFN) para Autômato Finito Deterministico (AFD).
- Minimização de estado do Deterministico (AFD).

## Análise léxica - ER para AFN
Utilização de fragmentos.  
Colar os diversos fragmentos para construir o autômato completo.  

![image](https://github.com/user-attachments/assets/5e5fb453-9807-4e6e-9158-f4b9eaabe593)

![image](https://github.com/user-attachments/assets/5cdb7425-ee5f-4c4c-926b-2f5949881603)

## Exercício 1
(a|b)*ac  
Qual é o AFN?

![image](https://github.com/user-attachments/assets/83795735-8c0a-44f2-83c5-91d65f946e59)

![image](https://github.com/user-attachments/assets/cb107a40-a390-47f1-a3c1-113836ba5282)

# Aula III

## Exercício II

![image](https://github.com/user-attachments/assets/78706f74-9789-4dfc-8d62-eea0b630ead4)

## Análise léxica - AFN para AFD
Simula todos os caminhos de um AFN simultaneamente.  
Criação de diversos “estados” de operação.  
Cada estado se tornará um único AFD.  

## Epsilon-states

Sempre que estivermos em um estado AFN, nós sempre poderemos ler um símbolo vazio.  
Assim, nos podemos usar uma transição vazia sem ler nenhum símbolo.  

## algoritmo

![image](https://github.com/user-attachments/assets/f17d44a7-5417-420c-9b98-feecfd87ad66)

## Exemplo 1

Passar o AFN do exercício 1 anterior para AFD.

(a|b)*ac -> AFD.

![image](https://github.com/user-attachments/assets/f271fc2c-5519-4c47-b652-341f804e460a)

E = {a,b,c}  
s'0 = {1,2,5,6,7}  
s'1 = {3,8,1,2,5,6,7}  
s'2 = {8,1,2,5,6,7}  
s'3 = {4}  

(s'0,a) = {3,8} U {1,2,5,6,7}  
s'1 = {3,8,1,2,5,6,7}  

(s'0,b) = {8} U {1,2,5,6,7}  
s'2 = {8,1,2,5,6,7}  

(s'0,c) = {∅} U {∅}  
∅  

(s'1,a) = {3,8} U {1,2,5,6,7}  
(s'1,a) = {3,8,1,2,5,6,7} = s'1  

(s'1,b) = {8} U {1,2,5,6,7}  
(s'1,b) = {8,1,2,5,6,7} = s'2  

(s'1,c) = {4} U {∅}  
s'3 = {4} -> como possui 4, s'3 é um estado final.  

(s'2,a) = {3,8} U {1,2,5,6,7}  
(s'2,a) = {3,8,1,2,5,6,7} = s'1  

(s'2,b) = {8} U {1,2,5,6,7}  
(s'2,b) = {8,1,2,5,6,7} = s'2  

(s'2,c) = {∅} U {∅}  
∅  

(s'3,a) = {∅} U {∅}  
∅  

(s'3,b) = {∅} U {∅}  
∅  

(s'3,c) = {∅} U {∅}  
∅  

Meu desenho:

![image](https://github.com/user-attachments/assets/bc0fcd78-b30f-4275-bcbe-3cf5ae965691)

**CORREÇÃO DO PROFESSOR**

![image](https://github.com/user-attachments/assets/f7dfa985-9ae9-4d9e-aef5-e2344341054a)
![image](https://github.com/user-attachments/assets/092c5fff-70b9-487e-8aea-4a5205613ac2)
![image](https://github.com/user-attachments/assets/01584dc7-a894-406f-8546-aea83584c4fc)
![image](https://github.com/user-attachments/assets/9be2c496-6151-4534-b663-0b972ea42f6c)
![image](https://github.com/user-attachments/assets/cbfb60b8-a611-485c-908d-0eb10ea747e2)
![image](https://github.com/user-attachments/assets/4129e891-0cd7-4001-9f2d-05667617013e)
![image](https://github.com/user-attachments/assets/24b0bcc7-24a5-4539-b2f5-3c84fb3f1aca)
![image](https://github.com/user-attachments/assets/3a0028a9-0317-46d4-a1be-339073d32df0)
![image](https://github.com/user-attachments/assets/83c75000-3346-42f0-a648-319d898098d7)
![image](https://github.com/user-attachments/assets/9f479910-6330-4d1a-889a-9a4423d71edb)
![image](https://github.com/user-attachments/assets/b6e02008-08e7-45d9-94c2-dcd7601c4c93)
![image](https://github.com/user-attachments/assets/4cfae1ac-83cc-4ed6-a492-215e7dba30d3)

### AFN e AFD

![image](https://github.com/user-attachments/assets/4b32e505-a8d3-4711-b2c0-97ba812cd062)


# Aula IV

## Exercíco 1

![image](https://github.com/user-attachments/assets/2939e7ec-5147-4a85-b5c5-74e66eef6d59)
![image](https://github.com/user-attachments/assets/02394ea5-0078-487c-b2e4-00b4b5e73cba)

E = {a,b}  
s'0 = {1,2,3,4,5}  
s'1 = {1,6,2,3,4,5}  
s'2 = {6}  
s'3 = {7,1,6,2,3,4,5}  
s'4 = {7}  
s'5 = {8,7,1,6,2,3,4,5}  
s'6 = {8}  

---------------------------------

(s'0,a) = {1,6} U {2,3,4,5}  
s'1 = {1,6,2,3,4,5}  
entenda como:  
s'0 percorrendo 'a' da {1,6}  
{1,6} percorrendo vazio da {2,3,4,5}  
Depois união de todos  
{1,6,2,3,4,5}.  

(s'0,b) = {6} U {∅}  
s'2 = {6}  
entenda como:  
s'0 percorrendo 'b' da {6}  
{6} percorrendo vazio da {∅}  
Depois união de todos  
{6}.  

(s'1,a) = {7,1,6} U {2,3,4,5}  
s'3 = {7,1,6,2,3,4,5}  
entenda como:  
s'1 percorrendo 'a' da {7,1,6}  
{7,1,6} percorrendo vazio da {2,3,4,5}  
Depois união de todos  
{7,1,6,2,3,4,5}.  

(s'1,b) = {6} U {∅}  
s'1,b = {6} = s'2  
entenda como:  
s'1 percorrendo 'b' da {6}  
{6} percorrendo vazio da {∅}  
Depois união de todos  
{6}.  

(s'2,a) = {7} U {∅}  
s'4 = {7}  

(s'2,b) = {∅} U {∅}  
∅  

(s'3,a) = {8,7,1,6} U {2,3,4,5}  
s'5 = {8,7,1,6,2,3,4,5} -> como possui 8 e 8 é estado final no AFN, s'5 é um estado final.  

(s'3,b) = {6} U {∅}  
s'3,b = {6} = s'2  

(s'4,a) = {8} U {∅}  
s'6 = {8} -> como possui 8, s'6 é um estado final.  

(s'4,b) = {∅} U {∅}  
∅  

(s'5,a) = {8,7,1,6} U {2,3,4,5}  
s'5,a = {8,7,1,6,2,3,4,5} = s'5  

(s'5,b) = {6} U {∅}  
s'5,b = {6} = s'2  

---------------------------------

Meu desenho:

![image](https://github.com/user-attachments/assets/a0698aad-6bc8-43a4-9150-f26fa806c27b)

---------------------------------

**CORREÇÃO DO PROFESSOR**

![image](https://github.com/user-attachments/assets/78a718b6-8724-4f9e-b804-668ae0073cb2)
![image](https://github.com/user-attachments/assets/2594c7fa-c3ab-4606-99fc-f980dc99d0b6)
![image](https://github.com/user-attachments/assets/3839d966-d95d-4830-ae1a-a39ef9f10fb8)

## Exercíco 2

![image](https://github.com/user-attachments/assets/56848985-f25b-4044-ba0e-86479a8f4e8c)

q0 percorrendo 0 vai para q0 (loop).  
q0 percorrendo 1 vai para q1.  

q1 percorrendo 1 vai para q1 (loop).  
q1 percorrendo 0 vai para q1 e q2 (criamos um estado q1q2).  

Obs: Podemos fazer operação de união como no slide:  
q1 percorre 0 -> {q1,q2}  
q2 percorre 0 -> {q2}  
União dos dois  
{q1,q2}

q2 percorrendo 0 vai para q2 - para não criar novo estado deixamos q1q2 (loop).  
q2 percorrendo 1 vai para q1q2 (loop)

q1 percorre 1 -> {q1}  
q2 percorre 1 -> {q1,q2}  
União dos dois  
{q1,q2}

![image](https://github.com/user-attachments/assets/31730da4-6061-4f64-a078-98bd739f498a)

## Exercíco 3

![image](https://github.com/user-attachments/assets/d211a206-3b31-424f-9d06-042b47a769b1)

q0 percorrendo 0 vai para q0 e q1 (criamos um estado q0q1).  
q0 percorrendo 1 vai para q1.  

q0q1 percorrendo 0 vai para q0q1 (loop).

q0 percorre 0 -> {q0,q1}  
q1 percorre 0 -> {∅}  
União dos dois  
{q0,q1}

q0q1 percorrendo 1 vai para q0q1 (loop).

q0 percorre 1 -> {q1}  
q1 percorre 1 -> {q1,q0}  
União dos dois  
{q0,q1}

q1 percorrendo 1 vai para q0 (podemos aproveitar o estado q0q1 já que o q1 faz parte do loop).

![image](https://github.com/user-attachments/assets/5f5d44a8-502d-49bc-9030-7a0fdd0eed47)

# Aula V

## Último exercício de AFN para AFD.

ER = a(a | bc)*

AFN = 
![ex 1 AFN](https://github.com/user-attachments/assets/f33d661d-1c30-43a5-9071-3129db443b86)

AFD = 

AFD:
E = {a,b,c}  
s'0 = {1}  
s'1 = {2,3,4,5,8}  
s'2 = {7,2,3,4,5,8}  
s'3 = {6}  

s'0 = {1} U {1}  
s'0 = {1}  

(s'0,a) = {2} U {3,4,5,8}  
s'1 = {2,3,4,5,8} -> tem 8, estado final  

(s'0,b) = {∅} U {∅}  
∅  

(s'0,c) = {∅} U {∅}  
∅  

(s'1,a) = {7} U {2,3,4,5,8}  
s'2 = {7,2,3,4,5,8} -> tem 8, estado final  

(s'1,b) = {6} U {∅}  
s'3 = {6}  

(s'1,c) = {∅} U {∅}  
∅  

(s'2,a) = {7} U {2,3,4,5,8}  
(s'2,a) = {7,2,3,4,5,8} = s'2  

(s'2,b) = {6} U {∅}  
(s'2,b) = {6} = s'3  

(s'2,c) = {∅} U {∅}  
∅  

(s'3,a) = {∅} U {∅}  
∅  

(s'3,b) = {∅} U {∅}  
∅  

(s'3,c) = {7} U {2,3,4,5,8}  
(s'3,c) = {7,2,3,4,5,8} = s'2  

![ex 1 AFD](https://github.com/user-attachments/assets/384058d1-a049-480b-a8fd-f41f1d853def)

Vídeo Auxiliar: [Assista](https://www.youtube.com/watch?v=paycBmJqwOs)

## Flex/Lex

É uma linaguagem de analisador léxico.

Existem 3 maneiras de construir um analisador léxico:
- Utilizar um gerador automático de analisadores léxicos.
- Escrever um analisador léxico utilizando uma linguagem de programação convencional.
- Escrever um analisador léxico utilizando uma linguagem de montagem.

## Linguagem Lex

Gerador automático de analisadores léxicos.

Também conhecida como Flex em uma implementação mais
recente.

Função:
- Diferenciar os diversos tipos de tokens através de ER
- Não verifica se todos as partes estão presentes
- Decidir como sub-dividir os tokens

## Estrutura de um programa Lex:

[definições]  
%%  
(expressão_regular [ação])*  
[%%  
funções auxiliares em C]  

![image](https://github.com/user-attachments/assets/85f57b05-8fda-4fe2-9f6e-332f2e2cb043)

![image](https://github.com/user-attachments/assets/4a6e7283-e7e7-48f3-a3ba-cad93e0293af)

![image](https://github.com/user-attachments/assets/8a55604e-114a-46b6-a427-2699a3841cc6)

![image](https://github.com/user-attachments/assets/0dfa6fe6-e97c-46b2-a787-732470eb12f3)

### Exemplos

![image](https://github.com/user-attachments/assets/324cbd86-f6ce-44bd-9a9f-97bcacd416e4)

![image](https://github.com/user-attachments/assets/fe199130-4691-463b-bb55-afcb1566646b)

![image](https://github.com/user-attachments/assets/621fc200-594b-4e25-9967-1d71df8cb947)

## Tente fazer

![image](https://github.com/user-attachments/assets/a1cc3695-e311-44f8-bc78-055a74389b70)

### Resposta

![image](https://github.com/user-attachments/assets/83e8651c-280f-4bc0-85a6-1370889ec4f7)

## Exercícios

![image](https://github.com/user-attachments/assets/0b76af52-3be3-40e0-821b-a184c3036e59)

### Exercício 1

![image](https://github.com/user-attachments/assets/2eb7ac01-0bad-49e7-bd4e-505410f2576f)

### Exercício 2

![image](https://github.com/user-attachments/assets/cd5bf6dc-97fe-462b-b667-6845b5660ebe)

### Exercício 3

![image](https://github.com/user-attachments/assets/8924b0f7-5f84-4d23-878e-e842ac42a6b4)

### Exercíco 4

![image](https://github.com/user-attachments/assets/c4792383-51f1-4cc1-bbd0-274ff10dd9fd)

### Exercíco 5

![image](https://github.com/user-attachments/assets/4fb9218b-77c4-4da1-b51c-17aa4599ca97)

### Exercíco 6

![image](https://github.com/user-attachments/assets/2dd8ccc8-7f7b-4e62-af71-4bfbd56e54f1)

## Exemplos de Análise Léxica

![image](https://github.com/user-attachments/assets/ed0926bd-1e69-4f8c-8972-cd1007511e31)

![image](https://github.com/user-attachments/assets/4437db3c-92ee-4d02-b73c-005603adb0f9)

## Exercícios


### Exercício 1

Código:  
```
while indice < 10 do
 indice:= total + indice;
```

Sequência de tokens:  
<while,> <id,7> <<,> <numero,10> <do,> <id,7> <:=,> <id,12> <+,> <id,7> <;, >

### Exercício 2

Código:  
```
position = initial + rate * 60
```

Sequência de tokens:  
<id, 1> <=, > <id, 2> <+, > <id, 3> <*, > <numero, 60>

### Exercício 3

Código:  
```
a[index] = 4 + 2
```

Sequência de tokens:  
<id, 1> <[,> <id, 2> <],> <=,> <numero, 4> <+,> <numero, 2>

### Exercício 4

Código:  
```
position = initial + rate * 60
```

Sequência de tokens:  
<id, 1> <=, > <id, 2> <+, > <id, 3> <*, > <numero, 60>

### Extra

Código:  
```
const a[book] = 5;
contador = 11;
while contador > 1 do {
	contador =- 1;
	if (contador <= 5) {
		a[contador] = contador + 2;
		print("numero inferior");
	}
}
contador *= 60;
```

Sequência de tokens:  
<const, > <id, 1> <[, > <id, 2} <], > <=, > <numero, 5> <;, >  
<id, 3> <=, > <numero, 11> <;, >  
<while, > <id, 3> <>, > <numero, 1> <> <do, > <{, >  
<id, 3> <=-, > <numero, 1> <;, >  
<if, > <(, > <id, 1> <<=,> <numero, 5> <), > <{, >  
<id, 1> <[, > <id, 1> <], > <=, > <id, 3> <+, > <numero, 2> <;, >  
<print, > <(, > <literal, "numero inferior"> <), > <;, >  
<}, >  
<}, >  
<id, 3> <*=, > <numero, 60> <;, >  