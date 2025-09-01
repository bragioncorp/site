---
title: "Exercícios de Algoritmo Genético"
excerpt: "Dois Exemplos de Exercícios de Algoritmo Genético."
categories:
  - IA
tags:
  - Inteligência Artificial
  - IA
  - Algoritmo Genético
  - GA
  - Exercícios

toc: true
---

# Problema 1

![image](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/11aacf88-569a-407c-addf-192aab7ac36d)

## Analisando

Este é mais tranquilo, pois não impõe nenhum limite e você já pode perceber que o máximo é 31.  
A função f(x) também é fácil.  
Usaremos quantas gerações precisar e apenas 1 ponto de corte.  
	
00 = 00000  
31 = 11111  
Cromossomo de 5 bits.  
Avaliação é a própria função.  

## 1ª Geração

- **Seleção do melhor indivíduo (maior avaliação):**  

indivíduos....x....f(x)	Pedaço da roleta (%)  
a1 = 10000  16	256		22,63%  
a2 = 11001  25	625		55,26%  
a3 = 01101  13	169		14,94%  
a4 = 01001  9   81		7,16%  

TOTAL f(x)		1131

**OBS: para calcular o pedaço da roleta:**

a1 = (256 / 1131) * 100 = 22,63%  
a2 = (625 / 1131) * 100 = 55,26%  
a3 = (169 / 1131) * 100 = 14,94%  
a4 = (81 / 1131) * 100 = 7,16%  

- **Melhores em ordem:**

11001, 10000, 01101 e 01001

- **Crossover (1 ponto) + mutação:**

110|01 -> 11000  
100|00 -> 10001 -> mutação -> 11001  

01|101 -> 01001 -> mutação -> 11001  
01|001 -> 01101

- **Filhos:**

11001 + 10000  =  11000 e 11001  
01101 + 01001  =  11001 e 01101

## 2ª Geração

- **Seleção do melhor indivíduo (maior avaliação):**

indivíduos....x....f(x)	Pedaço da roleta (%)  
a1 = 11000	24	576		28,87%  
a2 = 11001	25	625		31,32%  
a3 = 11001	25	625		31,32%  
a4 = 01101	13	169		8,47%  

TOTAL f(x)			1995  

- **Melhores em ordem:**

11001, 11001, 11000 e 01101  

- **Crossover (1 ponto) + mutação:**

11|001 -> 11001 -> mutação -> 11101  
11|001 -> 11001  

1100|0 -> 11001  
0110|1 -> 01100 -> mutação -> 11100  

- **Filhos:**

11001 + 11001  =  11101 e 11001  
11000 + 01101  =  11001 e 11100  

## 3ª Geração

- **Seleção do melhor indivíduo (maior avaliação):**

indivíduos....x....f(x)	Pedaço da roleta (%)  
a1 = 11101	29	841		29,25%  
a2 = 11001	25	625		21,73%  
a3 = 11001	25	625		21,73%  
a4 = 11100	28	784		27,26%  

TOTAL f(x)			2875

- **Melhores em ordem:**

11101, 11100, 11001 e 11001

- **Crossover (1 ponto) + mutação:**

1110|1 -> 11100  
1110|0 -> 11101 -> mutação -> 11111 (primeiro bom)  

11|001 -> 11001 -> mutação -> 11101  
11|001 -> 11001

- **Filhos:**

11101 + 11100  =  11100 e 11111   
11001 + 11001  =  11101 e 11001  

## 4ª Geração

- **Seleção do melhor indivíduo (maior avaliação):**

indivíduos....x....f(x)	Pedaço da roleta (%)  
a1 = 11100	28	784		26,17%  
a2 = 11111	31	961		32,08%  
a3 = 11001	25	625		20,86%  
a4 = 11001	25	625		20,86%  

TOTAL f(x)			2995

- **Melhores em ordem:**

11111, 11100, 11001 e 11001

- **Crossover (1 ponto) + mutação:**

1111|1 -> 11110 -> mutação -> 11111 (primeiro bom)  
1110|0 -> 11101  

1|1001 -> 11001  
1|1001 -> 11001 -> mutação -> 11101  

- **Filhos:**

11111 + 11100  =  11111 e 11101  
11001 + 11001  =  11001 e 11101  

## 5ª Geração

- **Seleção do melhor indivíduo (maior avaliação):**

indivíduos....x....f(x)	Pedaço da roleta (%)  
a1 = 11111	31	961		29,40%  
a2 = 11101	29	841		25,73%  
a3 = 11001	25	625		19,12%  
a4 = 11101	29	841		25,73%  

TOTAL f(x)			3268  

- **Melhores em ordem:**

11111, 11101, 11101 e 11001

- **Crossover (1 ponto) + mutação:**

1111|1 -> 11111 (primeiro bom)  
1110|1 -> 11101 -> mutação -> 11111 (segundo bom)  

1|1101 -> 11001  
1|1001 -> 11101 -> mutação -> 11111 (terceiro bom)  

- **Filhos:**

11111 + 11101  =  11111 e 11111  
11101 + 11001  =  11001 e 11111  

# Problema 2
![image](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/3c618a13-b236-43f2-b6d6-483064850bdc)

## Analisando

Encontrar ponto mínimo da função.

Considerar 4 indivíduos.  
Considerar 5 gerações.

f(x) = 2x - 3x + 4 =  
f(x) = - x + 4

x = [0, +7]

**Neste caso, dependendo do valor de "x", a função pode dar 0 ou um valor negativo. Para solucionar, incrementamos um valor:**

g(x) = 4 + f(x)  

0 = 000  
7 = 111  
cromossomo de 3 genes (bits).

## 1ª Geração

- **Seleção do melhor:**

indivíduos...x.....f(x)..g(x)...Pedaço da roleta (%)  
a1 = 000......0.....4.....8........25%  
a2 = 000......0.....4.....8........25%  
a3 = 000......0.....4.....8........25%  
a4 = 000......0.....4.....8........25%  

TOTAL f(x): 16  
TOTAL g(x): 32

- **Melhores:**

000 e 000

- **Crossover + mutação (2 reproduções dos 2 melhores):**

00|0	-> 000	->	mutação ->	010  
00|0	-> 000  

0|00	-> 000	->	mutação ->	001  
0|00	-> 000  

- **Filhos:**

010, 000, 001, 000

## 2ª Geração

- **Seleção do melhor:**

indivíduos...x.....f(x)..g(x)...Pedaço da roleta (%)  
a1 = 010......2.....2.....6........20,68%  
a2 = 000......0.....4.....8........27,58%  
a3 = 001......1.....3.....7........24,13%  
a4 = 000......0.....4.....8........27,58%  

TOTAL f(x): 13  
TOTAL g(x): 29
  
- **Melhores:**

000, 000, 001 e 010

- **Crossover + mutação:**

00|0	-> 000	->	mutação ->	010  
00|0	-> 000

0|01	-> 010  
0|10	-> 001	->	mutação ->	011

- **Filhos:**

010, 000, 010, 011

## 3ª Geração

- **Seleção do melhor:**

indivíduos...x.....f(x)..g(x)...Pedaço da roleta (%)  
a1 = 010......2.....2.....6........22,22%  
a2 = 000......0.....4.....8........29,62%  
a3 = 010......2.....2.....6........22,22%  
a4 = 011......3.....1.....5........18,51%  

TOTAL f(x): 9  
TOTAL g(x): 27

- **Melhores:**

000, 010, 010 e 011

- **Crossover + mutação:**

0|00	-> 010
0|10	-> 000 ->	mutação ->	100

0|10	-> 011
0|11	-> 010	->	mutação ->	110

- **Filhos:**

010, 100, 011, 110

## 4ª Geração

- **Seleção do melhor:**

indivíduos...x.....f(x)..g(x)...Pedaço da roleta (%)  
  a1 = 010......2.....2.....6........37,5%  
  a2 = 100......5....-1.....3........18,75%  
  a3 = 011......3.....1.....5........31,25%  
  a4 = 110......6....-2.....2........12,5%  

TOTAL f(x): 0   
TOTAL g(x): 16

- **Melhores:**

010, 011, 100 e 110

- **Crossover + mutação:**

01|0	-> 011 ->	mutação ->	111 (primeiro minimo)  
01|1	-> 010

1|00	-> 110	->	mutação ->	111 (segundo minimo)  
1|10	-> 100

- **Filhos:**

111, 010, 111 e 100

## 5ª Geração

- **Seleção do melhor:**
indivíduos...x.....f(x)..g(x)...Pedaço da roleta (%)  
a1 = 111......7....-3.....1........9,09%  
a2 = 010......2.....2.....6........54,54%  
a3 = 111......7....-3.....1........9,09%  
a4 = 100......5....-1.....3........27,27%  

TOTAL f(x): -5   
TOTAL g(x): 11

- **Melhores:**

010, 100, 111 e 111

- **Crossover + mutação:**

0|10	-> 000 -> mutação -> 100  
1|00	-> 110 -> mutação -> 111 (primeiro mínimo)

1|11	-> 111 (segundo mínimo)  
1|11	-> 111 (terceiro mínimo)

- **Filhos:**

100, 111, 111, 111

**Resposta final:**

Após 5 gerações, o ponto mínimo da função é 111, ou seja, x = 7 e f(x) = -3. Na última geração, 3 indivíduos são 111.