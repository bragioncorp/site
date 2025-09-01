---
title: "Compiladores - Resumão para P2"
excerpt: "Resumo Compiladores"
categories:
  - Compiladores
tags:
  - Compiladores
  - Resumo
  - Teoria
  - Análise Sintática

toc: true
---

# Aula VII

## Derivação

Sequência de substituições de não-terminais por uma escolha das regras de produção gramaticais.  

Método utilizado para a construção de uma cadeia específica de terminais, partindo de uma não-terminal inicial.  

Existem várias derivações para a construção da mesma cadeia de não-terminais.  

Verificar se a sequência de tokens é aceita:
- Inicia-se com um símbolo não-terminal chamado raiz.
- Aplica-se produções, substituindo não-terminais, até somente restarem terminais.
- Uma derivação substitui um não-terminal pelo lado direito de uma de suas produções.
- O símbolo " -> " denota um passo de derivação.

## Exemplo

![image](https://github.com/user-attachments/assets/96c6dd11-c73d-495c-8c7a-c64c62fa0401)

### Solução

![image](https://github.com/user-attachments/assets/197ac9c3-b56a-43f0-9fa5-6c3a99ff1b7e)

## À esquerda e à dirieta

Derivação mais à esquerda:  
é a sequência de formas sentenciais que se obtém derivando sempre o símbolo não-terminal mais à esquerda.  

Derivação mais à direita:  
é a sequência de formas sentenciais que se obtém derivando sempre o símbolo não-terminal mais à direita.  

### À esquerda

![image](https://github.com/user-attachments/assets/6d030460-fb58-4c75-8166-554ee58dcd0a)

### À direita

![image](https://github.com/user-attachments/assets/47a890f6-d203-4dcc-846e-a5c6d946a461)

Observe que o código final é o mesmo nos dois casos.

## Exercício 1

![image](https://github.com/user-attachments/assets/908bddb5-8a1c-4f4d-b5ad-c42cadc0149c)

### Solução

Apenas a 3

Por que 1 não está na gramática?  
Pois é impossível ter apenas 1 C após usar o Y.

Por que 2 não está na gramática?  
Pois é impossível ter 2 Cs sem B.

Por que 4 não está na gramática?  
Pois é impossível ter 3 Bs com apenas 2 Cs.

## Propriedades

A recursividade em uma GLC é importante, pois a possibilita a
construção da repetição.  

As produções vazias (ℇ - produções) são úteis para definir
estruturas opcionais da linguagem.  

## Ambiguidade

Quando existe mais de uma árvore de derivação para a mesma sentença.

Isso representa um problema para o analisador sintático, pois
ele não especifica com precisão a estrutura sintática do programa.

O problema pode ser comparado aos autômatos não determinísticos, onde dois caminhos podem aceitar a mesma cadeia

> Isso pode mudar todo o entendimento do comando -> mudar o if e else.

Porém, a eliminação de ambiguidade de uma gramática não é tão simples como a eliminação de não-determinismo em autômatos.

O que deve ser feito:
- Estabelecer uma regra que especifique para cada caso ambíguo qual é o caminho correto.

## Exemplo

![image](https://github.com/user-attachments/assets/9dcbae98-0c26-46cb-9201-44a9ef9f8497)

A ordenação das operações matemáticas está errada.

## Eliminação da ambiguidade

Eliminação de ambiguidade:
- Tratar conceitos de precedência e associatividade.
- Especificar uma ordem na avaliação dos operadores.
- Operadores com maior precedência são avaliados primeiro.
- Operadores de igual precedência são avaliados de acordo com a associatividade (esquerda-direita, vice-versa).

### Precedência
Agrupamentos dos operadores de igual precedência.

Para cada nível de precedência introduz-se um não terminal e uma regra gramatical.

### Associatividade

Cria-se regras gramaticais recursivas à esquerda ou à direita.

## Correção

![image](https://github.com/user-attachments/assets/38c221e0-3abe-4499-bf94-a88273c4ec1b)

## Exemplo 2

![image](https://github.com/user-attachments/assets/05e54e94-4335-4f96-b267-5e0808238e9b)

![image](https://github.com/user-attachments/assets/dde07ea9-2d6d-4fbe-a48d-cd16fb1d7a1c)

### Solução

A eliminação da ambiguidade pode ser feita a seguinte forma:

Associar cada ‘else' ao ‘if' mais próximo que ainda não tenha sido associado.

![image](https://github.com/user-attachments/assets/9bbea1c9-b5d8-4c73-b0bd-a6e939e58ca5)

## Exercício 2

![image](https://github.com/user-attachments/assets/59e1da8e-1e05-4f07-a75f-635b8f2a7fd0)

![image](https://github.com/user-attachments/assets/d32e2524-dbe3-4209-8769-e2332327bce4)

### Solução

É ambígua, pois não tem níveis diferentes, ou seja, a soma e a multiplicação possuem o mesmo nível de prioridade.

![image](https://github.com/user-attachments/assets/8408604d-7551-482d-8bc1-677b1e939574)

Primeira representação -> ambíguo.  
Segunda representação -> não ambíguo.  

## Exercício 3

![image](https://github.com/user-attachments/assets/9c636aa7-ea11-4f17-be38-0cacb2885b1c)

### Solução

![image](https://github.com/user-attachments/assets/ebdca84c-cfdb-46b4-a201-b02214031bff)

## Exercício 4

![image](https://github.com/user-attachments/assets/c0b6651f-3d10-44ae-9c62-08b3d57b626d)

### Solução

![image](https://github.com/user-attachments/assets/12111771-67b5-4608-bf94-91a8aba85582)

## Exercício 5

![image](https://github.com/user-attachments/assets/d93afc37-df75-4db5-a6f6-0a9c7846840f)

### Solução

G1 e G3 são ambíguas, pois possuem dois símbolos não-terminais (S) do lado direito.

G2 apresente apenas 1, por isso não é.

# Aula VIII

## Notação BNF

Uma das representações formais utilizadas para descrever a sintaxe de uma linguagem.

Desenvolvida por John Backus e Peter Naur.

É possível construir um parser (analisador sintático) automaticamente com apenas a gramática em BNF.

- Símbolos não-terminais são representados por textos delimitados por "<" e ">".

- O meta-spimbolo " -> " é substituido por " ::= ".

- Todas as alternativas de substituição para um mesmo não-terminal são agrupadas, separando-as com | .

### Exemplo

![image](https://github.com/user-attachments/assets/49e496c6-8e40-46cb-bba5-66fbd3456ef4)

### Exemplo 2

![image](https://github.com/user-attachments/assets/28dc3295-adc4-427f-bae6-61f76d850543)

## BNF estendida com fecho transitivo

" * " = operação de fecho

![image](https://github.com/user-attachments/assets/1e7ee241-05eb-4e13-834f-b04b38ea165e)

### 1º 

linha < X > ::= a< X >|a

ao invés de ficar na recursão "X" deriva "aX" ou "a" (infinitos "a"s), podemos reduzir ao símbolo mínimo ("a"), ou seja, "X" deriva " aa* ".

> " aa* " já está passando a ideia da recursão.

então fica < X > ::= aa*

### 2º

linha < Z > ::= cd< Z >|e< Z >|f

ao invés de ficar na recursão "Z" deriva "cd<Z>" ou "e<Z>" (infinitos "cd"s e "e"s), podemos reduzir ao símbolo mínimo (" (cd|e)* , ou seja, "Z" deriva " (cd|e)* | f ".

> " (cd | e)* " já está passando a ideia da recursão.

então fica < Z > ::= (cd|e)*|f

## Simplificando ainda mais

![image](https://github.com/user-attachments/assets/580029d6-9865-4587-9d52-a9811e1cbbdc)

![image](https://github.com/user-attachments/assets/1b642124-15cd-4aca-a785-187c9a7fc4f3)

## BNF extensões

" [ a ] " -> "a" opcional.

" [ a | b ] " -> "a" ou "b" opcionais.

" { a | b } " -> vários itens ("a" ou "b").

" {";" <statement>} " -> várias sequencias de comandos.

### Exemplo

![image](https://github.com/user-attachments/assets/b71740bb-a61b-4faa-9e16-2744cb03c338)

## Exercício 1

BNF:

< S > ::= (< M >) | a | b  
< M > ::= < M >;< N > | < N >  
< N > ::= < N >,< S > | < S >  

Qual a representação formal?

### Solução

Representação formal:

G = (V, T, P, S)

G = ({M,N,S}, {a, b, (, ), "," , ;}, P, S)

P = {  
S -> (M) | a | b  
M -> M;N | N  
N -> N,S | S  
}


## Exercício 2

Gramática:

G = (Vt, Vn, P, S), sendo:

Vt = {a, b},  
Vn = {A, S},  
P = {S -> A, A -> aAb, A -> ab}

Qual a gramática em notação BNF?

### Solução

BNF:

< S > ::= < A >  
< A > ::= a< A >b  
< A > ::= ab  

## Autômato com pilha

Parser é definido através de uma gramática livre de contexto, o que nos obriga a utilizar um autômato a pilha na sua implementação.

O autômato a pilha é a ferramenta básica na construção do parser.

### Estrutura da pilha

![image](https://github.com/user-attachments/assets/5bf06e92-76e9-4eae-861f-f6ec85f1d2b7)

### Como funciona?

Dependendo do estado corrente, símbolo da fita e símbolo da pilha, determina o novo estado e a palavra a ser gravada na pilha.

Um AP é definido pela 6-tupla:  

![image](https://github.com/user-attachments/assets/c736e24b-be51-4d65-8305-e883d4c28b59)

E = alfabeto  
Q = conjunto de estados  
& = funções transição  
q0 = estado inicial  
F = estados finais  
V = alfabeto da pilha  

![image](https://github.com/user-attachments/assets/df6bfe22-1f25-4f99-8988-9f2a63812d84)

## Observação

![image](https://github.com/user-attachments/assets/4861adae-b511-4cad-9007-4946d9064f53)

## Exemplo

![image](https://github.com/user-attachments/assets/5ef73762-05e0-40a5-bd05-964911eb2505)

## Construindo um AP

1) pilha começa não vazio - tem simbolo inicial (símbolo inicial da gramática).  
2) apenas 1 estado - aceitação de pilha vazia.  
2.1) &(q,x,x) = (q,λ), para cada simbolo (x) do alfabeto do alfabeto.  
2.2) para cada A -> y, a transição &(q,λ,A) = (q,y).  

## Exemplo

![image](https://github.com/user-attachments/assets/2eba6e07-10b0-49e1-a4f7-54854d135265)

![image](https://github.com/user-attachments/assets/b7b69c26-07be-48cf-b0d4-66cdfc7fa7f6)

![image](https://github.com/user-attachments/assets/ba09d304-3b26-4e28-9837-cb9b0eb8fe3d)

## Exemplo 2

![image](https://github.com/user-attachments/assets/f3a7a2bc-35b8-4db2-8f2b-0a5d3517c756)

![image](https://github.com/user-attachments/assets/20a469d9-3d84-4389-86fb-2c49b198eade)

![image](https://github.com/user-attachments/assets/6e885c76-79bf-444c-a5ed-ce1509bb18f5)

# Aula 10

## Exercício

![image](https://github.com/user-attachments/assets/d7e08ec0-a08b-48d1-8119-e5c55ce8d9b5)

![image](https://github.com/user-attachments/assets/7b2968bd-9e0c-4bae-ab2f-b7b21f0bfd7f)

Árvore sintática gerada

![image](https://github.com/user-attachments/assets/213cdb4e-850b-452d-a7b0-cc82c7e9248c)

## Análise sintática descendente

- Toma-se uma determinada palavra P e o símbolo inicial S da gramática.

- Procura-se por uma regra de derivação que permita derivar P em sua totalidade ou pelo menos se aproximar desta.

- Repetir o passo acima até que a palavra P não apresente mais símbolos não-terminais.

- Por fim, verifica-se se a cadeia obtida coincide com P. No caso negativo, tem-se que a cadeia analisada não pertence a linguagem.

## Analisador sintático preditor

- O analisador recebe uma sequência de entrada.

- Manipula uma estrutura de dados tipo pilha.

- Para cada símbolo de entrada, consulta uma tabela de análise sintática para aplicação da regra.

- Emite uma sequência de saída (regras).

![image](https://github.com/user-attachments/assets/9d153867-e99c-47a1-a49b-fd4121996d83)


## Observações:

### Entrada

Sentença a ser analisada seguida pelo delimitador $.

Pilha: contém uma sequência de símbolos da gramática precedida pelo indicador de base de pilha $.

TAS: é uma matriz M[A,a], onde A é um não-terminal e a é um terminal ou dólar $.

> O topo da pilha é na direita

### Saída

Constará as produções aplicadas a partir do símbolo inicial (S) na geração da sentença.

## Regras

- 1 - Se X é um terminal = próximo_símbolo = $, o analisador encerra sua atividade e comunica fim da análise sintática com sucesso.

- 2 - Se X é um terminal = próximo_símbolo ≠ $, o analisador elimina X do topo da pilha e avança para o próximo símbolo de entrada.

- 3 - Se X é um terminal ≠ próximo_símbolo, o analisador acusa um erro de sintaxe (ativa rotina de tratamento de erros).

- 4 - Se X é um não-terminal, o analisador consulta M[X,próximo_símbolo]

  a) Se a resposta for uma regra de produção X ::= MVU, o analisador desempilha X do topo da pilha e empilha UVM, sendo M no topo da pilha.

  b) Se M[X, próximo_símbolo] = ERRO, o analisador acusa um erro de sintaxe e ativa rotina de tratamento de erros.

## Exemplo 1

![image](https://github.com/user-attachments/assets/1cba062c-8763-4f4d-9b96-0145a9f1b97a)

![image](https://github.com/user-attachments/assets/c7e5cf62-b788-42e7-a255-cc74c4e89172)

![image](https://github.com/user-attachments/assets/ddaa1cb3-036b-4654-af52-b1d82e69b21d)

## Exercício 1

![image](https://github.com/user-attachments/assets/100cee69-0bc8-4453-97fa-9a7a7c473afb)

![image](https://github.com/user-attachments/assets/7d28c2f4-f27e-4c2b-9bbe-572a93acbfeb)

## Exercício 2

![image](https://github.com/user-attachments/assets/bfde5984-f410-40da-b802-757e2b32a82b)

![image](https://github.com/user-attachments/assets/31b52385-e8ac-42f9-ab0c-fb1388ead6b9)

## Exercício 3

![image](https://github.com/user-attachments/assets/aac5554b-c69c-454b-ae75-9b84e8155736)

![image](https://github.com/user-attachments/assets/7928d08d-b790-47df-a4a9-85ff5928b064)


![image](https://github.com/user-attachments/assets/79d5f8d2-f89b-4b33-8a34-ac914f97efb7)

## Exercício 4

![image](https://github.com/user-attachments/assets/03489ed3-8477-4ca3-9a2d-a79547a75dcc)

![image](https://github.com/user-attachments/assets/09e18c86-566d-45b2-8bff-89a239221033)

Da erro, não é possível completar.

# Aula 11

## Como construir a tabela?

Analisador preditor
- conjunto FIRST
- conjunto FOLLOW

## Etapas do analisador preditor

Durante análise descendente -> as variáveis FIRST e FOLLOW nos ajudam a escolher qual produção deve ser usada, com base no próxim símbolo de entrada.

Dada uma entrada 'a' e o não-terminal 'A', deve-se saber qual das produções alternativas 'A -> B1 | B2 | ...' deriva a sequência que inicia por 'a'.

Primeiro são calculados os conjuntos de primeiros símbolos produzios por todas as alternativas na gramática, ou seja, os conjuntos FIRST.

Sendo Y uma string de símbolos e não-terminas, FIRS(Y) é o conjunto de todos os terminais que podem iniciar strings derivadas de Y.

## Algoritmo geral

![image](https://github.com/user-attachments/assets/a4fb4857-6469-48ee-aa8d-8badae7e6ac8)

## Regras do FIRST

![image](https://github.com/user-attachments/assets/535af31f-2526-4f9d-9eb9-fba5bdeaa9eb)

## Exemplo 1

![image](https://github.com/user-attachments/assets/cd9fed41-8ff2-42e2-8d45-397530539227)

### Tabela inicial

Todos os símbolos não-terminais iniciam com vazio.

![image](https://github.com/user-attachments/assets/210cc31c-1f85-439a-9228-59d5b4903f6a)

Nota: λ = E (vazio).

### Calculando 'S'

Firts(S) = First(ABS) U First(aA)

First(ABS) = First(A) \ {λ}  
First(ABS) = ∅ \ {λ}  
First(ABS) = ∅  

> Calculou apenas o 'A' de 'ABS', pois 'A' não possui 'λ', então não precisa calcular o 'B'.

First(aA) = First(a) \ {λ}  
First(aA) = {a} \ {λ}  
First(aA) = {a}  

> Calculou apenas o 'a' de 'aA', pois 'a' não possui 'λ', então não precisa calcular o 'A'.

**First(S) = {a}**

### Calculando 'A'

First(A) = First(λ) U First(a)

First(λ) = {λ}
First(a) = {a}

**First(A) = {λ,a}**

### Calculando 'B'

First(B) = First(Bb) + First(cd)

First(Bb) = First(B) \ {λ}  
First(Bb) = ∅ \ {λ}  
First(Bb) = ∅  

> Calculou apenas o 'B' de 'Bb', pois 'B' não possui 'λ', então não precisa calcular o 'b'.

First(cd) = First(c) \ {λ}  
First(cd) = {c} \ {λ}  
First(cd) = {c}  

> Calculou apenas o 'c' de 'cd', pois 'c' não possui 'λ', então não precisa calcular o 'd'.

**First(B) = {c}**

### Nova tabela

![image](https://github.com/user-attachments/assets/afb790a0-88d0-479a-8ff7-8a4eec1b13a3)

### Recalcular

Como FIRST de 'S' depende de 'A' e 'A' teve seu valor alterado, devemos recalcular 'S'.


### Calculando 'S'

Firts(S) = First(ABS) U First(aA)

First(ABS) = First(A) \ {λ}  
First(ABS) = {λ,a} \ {λ}  

> First(A) agora tem 'λ', então vamos calcular o First(B).

First(ABS) = {a} U First(B) \ {λ}  
First(ABS) = {a} + {c}  

First(aA} = {a}

**First(S) = {a,c}**

### Nova tabela 2

![image](https://github.com/user-attachments/assets/b0ec40d9-0654-4aae-8bfd-a8f099c34654)

## Exemplo 2

![image](https://github.com/user-attachments/assets/63c952f8-05e3-4c33-b06d-c07810d73d1a)

First(S) = First(cAd) = {c}  
First(A) = First(b) U First(a) = {b,a}

## Exemplo 3

![image](https://github.com/user-attachments/assets/8033beab-06c0-45f8-9454-ca8bbd46f074)

Podemos simplificar

Z ::= d | XYZ  
Y ::= λ | c  
X ::= Y | a  

### Tabela inicial

Z = ∅  
Y = ∅  
X = ∅  
XYZ = ∅  

### Calculando 'Z'

First(Z) = First(d) U First(XYZ)  
First(Z) = {d} U {∅}  
**First(Z) = {d}**  

First(Y) = First(λ) U First(c)  
First(Y) = {λ} U {c}  
**First(Y) = {λ,c}**  

First(X) = First(Y) U First(a)  
First(X) = {λ,c} U {a}  
**First(X) = {λ,c,a}**  

### Nova tabela

First(Z) = {d}  
First(Y) = {λ,c}  
First(X) = {λ,c,a}  

### Recalculando Z

First(Z) = First(d) U First(XYZ)  
First(Z) = {d} U First(X) \ {λ} U First(YZ)  
First(Z) = {d} U {c,a} U First(Y) \ {λ} U First(Z)  
First(Z) = {d} U {c,a} U {c} U First(Z) \ {λ}  
First(Z) = {d} U {c,a} U {c} U {d}  
**First(Z) = {c,a,d}**  

### Nova tabela 2

First(Z) = {c,a,d}  
First(Y) = {λ,c}  
First(X) = {λ,c,a}  

## Exemplo 4

![image](https://github.com/user-attachments/assets/39defccb-d1e9-4b31-b1d9-fcd5339403e4)

Podemos simplificar

S ::= AaAb | Bb  
A ::= λ  
B ::= λ  

### Tabela inicial

S = ∅  
A = ∅  
B = ∅  

### Calculando S

First(S) = First(AaAb) U First(B)  
First(S) = First(A) U First(B)  
First(S) = {∅} U {∅}  
**First(S) = {∅}**  

### Calculando A

**First(A) = {λ}**  

### Calculando B

**First(B) = {λ}**  

### Nova tabela

First(S) = {∅}  
First(A) = {λ}  
First(B) = {λ}  

### Recalculando S

First(S) = First(AaAb) U First(B)  
First(S) = First(A) \ {λ} U First (aAb) U First(B) U First(b)  
First(S) = {a} U {b}  
**First(S) = {a,b}**  

### Nova tabela 2

First(S) = {a,b}  
First(A) = {λ}  
First(B) = {λ}  

## Exemplo 5

![image](https://github.com/user-attachments/assets/1bed62e8-9100-46ec-abce-2053fa72a36e)

S -> cAa  
A -> cB | B  
B -> bcB | λ  

### Tabela inicial

S = ∅  
A = ∅  
B = ∅  

First(B) = First(bcB) U First(λ)  
First(B) = {b} U {λ}  
First(B) = {b,λ}  

First(A) = First(cB) U First(B)  
First(A) = {c} U {b,λ}  
First(A) = {c,b,λ}  

First(S) = First(cAa)  
First(S) = {c}  

### Nova tabela

S = {c}  
A = {b,c,λ}  
B = {b,λ}  

## Exercício

![image](https://github.com/user-attachments/assets/50a55545-7afc-4f9b-b21b-0e7a0ef257cf)

S -> aS | Ab  
A -> XYZ | λ  
X -> cS | λ  
Y -> dS | λ
Z -> eS  

### Tabela inicial

S = ∅  
A = ∅  
X = ∅  
Y = ∅  
Z = ∅  

First(Z) = First(eS)  
First(Z) = {e}  

First(Y) = First(dS) U First(λ)  
First(Y) = {d} U {λ}  
First(Y) = {d,λ}  

First(X) = First(cS) U First(λ)  
First(X) = {c} U {λ}  
First(X) = {c,λ}  

First(A) = First(XYZ) U First(λ)  
First(A) = First(X) \ {λ} U First(Y) \ {λ} U First(Z) U First(λ)  
First(A) = {c} U {d} U {e} U {λ}  
First(A) = {c,d,e,λ}  

First(S) = First(aS) U First(Ab)  
First(S) = {a} U First(A) \ {λ} U First(b)  
First(S) = {a} U {c,d,e} U {b}  
First(S) = {a,b,c,d,e}  

### Nova tabela

First(S) = {a,b,c,d,e}  
First(A) = {c,d,e,λ}  
First(X) = {c,λ}  
First(Y) = {d,λ}  
First(Z) = {e}  

## Aula 12

Conjunto Follow.  
Criação da tabela preditiva.  

## FOLLOW - Regras

![image](https://github.com/user-attachments/assets/21b3a695-ea6d-4fdd-a49a-1286a34f7410)

![image](https://github.com/user-attachments/assets/cff75ebe-1c40-46d0-a30d-cb679ecc6992)

follow(S) = {$}  

follow(A) = First(b) \ {λ}  
follow(A) = {b}  

follow(Z) = follow(A)  
follow(Z) = {b}  

follow(Y) = first(Z)  
follow(Y) = {e}  

follow(X) = first(Y) U first(Z)  
follow(x) = {d,λ} U {e}  
follow(x) = {d,e}  

Recalculando S

follow(S) = follow(X) U follow(Y) U follow(Z)  
follow(S) = {$,b,d,e}  

![image](https://github.com/user-attachments/assets/64a2d23b-e3da-42e6-b799-87cefc64b053)

Como o 'S' é o símbolo inicial, Follow(S) recebe '$' e deixamos o resto por último.  

Follow(A) é 'b' pois em 'S' temos 'A' com 'b' em seguida (lado direito).  

Follow(Z) é 'b' pois eu tenho 'Z' em 'XYZ', como não tem nada do lado direito, pega o mesmo valor de FOLLOW(A).  

Follow(Y) é 'e' pois o FIRST(Z) é 'e' (pegou o FIRST pois o 'Z' está no lado direito).  

Follow(X) é 'd,e' pois temos 'Y' e 'Z' no lado direito e o First de 'Y' e 'Z' é 'd,λ' e 'e' respectivamente (só calculou o First de Z pois Y tem palavra vazia).

Agora, vamos recalcular o Follow(S), que é '$' com a soma do Follow(X), Follow(Y) e Follow(Z) (pois S não tem nada do lado direito então pega X, Y e Z),resultando em '$,b,d,e'.

## Exercício ENADE

![image](https://github.com/user-attachments/assets/cc7e08d3-df20-4426-b753-8e50415a0451)

![image](https://github.com/user-attachments/assets/00d60cc4-837b-448c-b033-e55b93ee7402)

## Tabela preditiva M(X,t)

![image](https://github.com/user-attachments/assets/f75235a4-3af0-4f98-822a-3454372c62b6)

![image](https://github.com/user-attachments/assets/148a3789-2d30-41e6-8d5b-c8ef261d4fc3)

## Exemplo 1

![image](https://github.com/user-attachments/assets/62bc2379-c0f0-4a0f-b1b1-4e2f078ebe29)

---

Linha 'S'.

First(cAa) = {c}, por isso a localização em 'S', 'c'.

![image](https://github.com/user-attachments/assets/415fe353-8829-4316-bb41-f6aa034ede5d)

---

Linha 'A'.

First(B) = {b,λ}, por isso a localização em 'A', 'b'.

![image](https://github.com/user-attachments/assets/3b0ad56e-fe29-459a-9d39-1629a0cfef10)

---

Como First(B) tem {λ}, analisamos o Follow(B) = {a}, ou seja, também coloca em 'A', 'a'.

![image](https://github.com/user-attachments/assets/9b2e6c90-efb9-4f66-90ff-0656ea2aa6d7)

---

First(cB) = {c}, por isso a localização em 'A', 'c'.

![image](https://github.com/user-attachments/assets/0ade5d69-51ee-4998-94b3-dc441dbf1574)

---

Linha 'B'

First(λ) = {λ}, analisamos o Follow(B) = {a}, por isso a localização em 'B', 'a'.

![image](https://github.com/user-attachments/assets/25c3343f-99b9-4e25-8f70-2a5cf3d245d2)

---

First(bcB) = {b}, por isso a localização em 'B', 'b'.

![image](https://github.com/user-attachments/assets/85da962a-7766-4170-9df8-bf89e01516e9)

---

O resto é erro.

![image](https://github.com/user-attachments/assets/dde50697-9691-4d92-b811-80fc200378fc)

## Exercício 1

![image](https://github.com/user-attachments/assets/d4573c30-504a-4e8b-bd14-757f34fbdc4b)

---
FIRST

First(A) = First(λ)  
First(A) = {λ}  

First(B) = First(λ)  
First(B) = {λ}  

First(S) = First(AaAb) U First(Bb)  
First(S) = First(AaAb) \ {λ} U First(Bb) \ {λ}  
First(S) = {a} U {b}
First(S) = {a,b}

FOLLOW

Follow(S) = {$}

Não existe 'S' em nenhuma outra parte, então fica assim.

Follow(A) = First(aAb) \ {λ} U First(b) \ {λ}  
Follow(A) = {a} U {b}  
Follow(A) = {a,b}  

Follow(B) = First(b)  
Follow(B) = {b} \ {λ}  
Follow(B) = {b}  

![image](https://github.com/user-attachments/assets/7963ff01-c739-42c7-a9a7-537af0fd8287)

![image](https://github.com/user-attachments/assets/e6c99658-4c33-4b72-bc27-d0432d5b1dad)

## Exercício 2

![image](https://github.com/user-attachments/assets/f8b8d244-8768-4a1c-9c9d-a8e9c813b02a)

---

Linha Z

First(eS) é {s}, logo, 'Z -> eS' vai em 'Z,e'

---

Linha Y

First(dS) é {d}, logo, 'Y -> dS' vai em 'Y,d'

Como tem {λ}, devemos seguir Follow(Y) que é {e}, , logo, 'Y -> λ' vai em 'Y,e'

---

Linha X

First(cS) é {c}, logo, 'X -> cS' vai em 'X,c'

Como tem {λ}, devemos seguir Follow(X) que é {d,e}, , logo, 'X -> λ' vai em 'X,d' e 'X,e'

---

Linha A

First(XYZ) é {c,d,e}, logo, 'A -> XYZ' vai em 'A,c', 'A,d' e 'A,e'

Como tem {λ}, devemos seguir Follow(A) que é {b}, , logo, 'A -> λ' vai em 'A,b'

---

Linha S

First(aS) é {a}, logo, 'S -> aS' vai em 'S,a'

First(Ab) é {c,d,e,λ}, e como possui {λ}, calculamos o {b} também, então 'S -> Ab' vai em 'S,b', 'S,c', 'S,d', 'S,e'

![image](https://github.com/user-attachments/assets/7b253809-7a95-4d0d-8a43-88a91df669d4)

## Exercícios para treinar

![image](https://github.com/user-attachments/assets/3f510735-e6eb-44f5-b4f1-6c9c28faca0c)

...

# Aula 13

## Analisador semântico

Verifica o uso de:

- Análise contextual - declarações prévias de variáveis, procedimentos, etc
- Checagem de tipos - o tipo da variável é o correto para o operador?
- Unicidade - o identificador é único no escopo?

![image](https://github.com/user-attachments/assets/d005f890-e579-4e4b-9580-72a332a3535f)

## Verificações semânticas

- X foi declarado apenas uma vez?
- X foi declarado/definido antes do seu primeiro uso?
- X é um tipo escalar, um array, uma função, ou uma classe?
- X é declarado mais nunca utilizado?
- A que declaração X se refere?
- Os tipos de uma expressão são compatíveis?
- As dimensões casam com o declarado?

## Tipos de análise semânticas

- Estática: em tempo de compilação (linguagens tipadas).
- Dinâmica: em tempo de execução (variáveis são determinadas pelo con texto de uso).

## Gramática de atributos

Identifica quais ações serão realizadas em relação ao:

- comportamento semântico das operações
- checagem de tipos
- manipulação de erros
- tradução do programa

## Tabela de símbolos

Permite saber durante a compilação de um programa:

- tipo e endereço dos elementos
- escopo dos elementos
- número e tipo dos parâmetros de um procedimento

## Gramática de atributos

Uma das formas de descrever a semântica.

- São agregados atributos aos símbolos não-terminais da gramática.
- São agregadas regras semânticas às produções da gramática, as quais computam os valores dos atributos dos símbolos.

## Atributos VS Regras Semânticas

Atributos: elementos associados aos símbolos gramaticais.

- Ex: valor e escopo, representados na forma x.valor, x.escopo

Regras semânticas: manipulam os atributos

- Ex.: regra para somar os atributos valores de 2 variáveis -> x:=a+b, cuja regra é x.valor:=a.valor+b.valor

## Amarração

Atributos podem ser fixados durante a compilação ou na
execução do programa.

A associação de um valor a um atributo é chamada “amarração”
do atributo.

Acontece em “tempo de amarração”:

– Em tempo de compilação, amarração estática
– Em tempo de execução, amarração dinâmica

## Exemplo 1

![image](https://github.com/user-attachments/assets/2b4a83e7-6c05-493f-afe4-ad1540d1d748)

![image](https://github.com/user-attachments/assets/d2549fec-b616-437e-974c-cb37cf8b72dd)

![image](https://github.com/user-attachments/assets/42178ebf-d917-468e-87fe-c88dad8ced68)

![image](https://github.com/user-attachments/assets/7bb5645a-b5b5-4303-a1c0-ae169a30112b)

Cálculo dos atributos

![image](https://github.com/user-attachments/assets/50f96d56-5c65-4c6b-a90f-511e1e21fa3c)

![image](https://github.com/user-attachments/assets/66c7d9a8-dfdf-4c46-b093-247f6cd9e099)

## Exercício 1

![image](https://github.com/user-attachments/assets/17eca46e-bd35-44e5-b0c4-51c30a817da9)

![image](https://github.com/user-attachments/assets/b3ab9a12-815c-4be3-9abf-38a55dd803ce)

![image](https://github.com/user-attachments/assets/034570d9-6fd2-46f8-9e00-5b523939d178)

![image](https://github.com/user-attachments/assets/f81e1cbd-de3d-40d7-924b-8908eb733f79)

![image](https://github.com/user-attachments/assets/ba86e8d0-b27f-4547-a5c7-2ce5fc895b7a)

## Exercício 2

![image](https://github.com/user-attachments/assets/d83aa8cb-56aa-4851-b146-7698cbc1bf04)

![image](https://github.com/user-attachments/assets/bae56889-6020-43cd-a483-555dd1124124)

![image](https://github.com/user-attachments/assets/d9c8040c-2d59-41d4-8114-c31ff200eba3)

## Exercício Extra

![image](https://github.com/user-attachments/assets/d9679f7c-e474-4f8a-abff-7eb4d67bb00d)
