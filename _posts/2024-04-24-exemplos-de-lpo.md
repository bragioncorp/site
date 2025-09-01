---
title: "Exemplos de LPO"
excerpt: "Alguns exemplos de LPO para praticar."
categories:
  - IA
tags:
  - IA
  - Inteligência Artificial
  - LPO
  - Exemplos LPO
  - P1

toc: true
---

## Lógica de Primeira Ordem

É elaborada em torno de objetos e relações.  
Principal diferença entre lógica proposicional (LP) e lógica de primeira ordem (LPO) é o compromisso ontológico, ou seja, o que cada linguagem pressupõe sobre a natureza da realidade.  

> LP: pressupõe que existem fatos que são válidos ou não válidos no mundo.  
> LPO: pressupõe que o mundo consiste em objetos com certas relações entre eles que são válidas ou não-válidas.  

Lembrando que:  

> ⋀ = E lógico  
> ⋁ = OU lógico  
> ∀x = para todo x  
> ∃x = para algum x  
> ¬ = negação  
> ⇒ = implicação lógica  
> ⟺ = equivalência lógica  
> ≣  = estritamente equivalente  

### Exemplo das Cenouras

    ∀x ¬Gosta(x,Cenouras) ≣ ¬∃x Gosta(x,Cenouras) =
    “todo mundo detesta cenouras” =
    “não existe alguém que goste de cenouras”.

    ∀x¬P ≣ ¬∃xP

### Exemplo dos Sorvetes

    ∀x Gosta(x,Sorvete) ≣ ¬∃x ¬Gosta(x,Sorvete) =
    “todo mundo gosta de sorvete” =
    “não existe alguém que não goste de sorvete”

    ∀xP ≣ ¬∃x¬P

### Para todo departamento, há pelo menos um funcionário que é chefe.

    ∀x Departamento(x) ^ ∃y Funcionario(y) ⇒ Chefe(y, x)

### Algumas pessoas gostam de todos os tipos de música.

    ∃x Pessoas(x) ^ ∀y Música(y) ⇒ (Gosta(x, y))

### Existe um aluno que não está matriculado em nenhum curso.

    ∃x Aluno(x) ^ ∀y Curso(y) ⇒ ¬Matriculado(x, y)

### Todos os alunos estudam matemática.

    ∀x Aluno(x) ⇒ Estuda(x, matemática)

### Existe um estudante que gosta de todas as disciplinas.

    ∃x Estudante(x) ^ ∀y Disciplinas(y) ⇒ Gostar(x, y)