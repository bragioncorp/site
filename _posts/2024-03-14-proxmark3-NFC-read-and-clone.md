---
title: "Usando Proxmark3 para ler e emular NFC"
excerpt: "Aprenda como ler TAG ou cartão NFC e emular seu conteúdo usando o Proxmark3."
categories:
  - Hacking
tags:
  - Proxmark3
  - NFC
  - Ler e Emular
  - Ler NFC
  - Emular NFC
  - TAG NFC
  - Cartão NFC

toc: true
---

## Usando o Proxmark3 para emular cartão NFC

Etapas simples para escrever uma URL em uma TAG ou cartão NFC usando o software "NFC Tools" no Android, como clonar este conteúdo (URL) e emular usando o Proxmark3.  

### Início

  Instale o NFC Tools no seu celular.  
  Leia alguma tag e escreva algum link (também pelo celular).  

### Força-bruta + leitura das chaves/setores.

  hf mf autopwn

### Salve os dados na memória do emulador.

  hf mf esave

### Veja o conteúdo da memória (URL e outros dados).

  hf mf review

### Simule/emute o cartão MIFRA CLASSIC 1k usando o Proxmark3

  hf mf yes --1k

### Exeucção
Aproxime o seu celular com hardware de leitura NFC (nativo, celulares modernos) e abra o link.