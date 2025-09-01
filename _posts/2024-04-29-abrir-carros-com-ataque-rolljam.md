---
title: "Abrindo Carros com Ataque Rolljam"
excerpt: "Teoria sobre como abrir carros usando o ataque rolljam."
categories:
  - Hacking
tags:
  - Rolljam
  - Ataque Rolljam
  - Carros
  - Evil Crow RF V2
  - HackRF One
  - Yard Stick One
  - RTL-SDR

toc: true
---

# Explicação rápida
Aqui será explicado a teoria de como destrancar um carro através de bloqueios, capturas e retransmissões (replay) do código enviado pela chave.

## Rolling Codes
O código enviado pela chave do carro é único, ou seja, transmitir o mesmo código para abrir ou trancar o carro várias vezes não vai funcionar. Isso acontece por causa do Rolling Code, ou seja, um código que é usado em sistemas de entrada sem chave para evitar uma forma simples de ataque de repetição, onde um agente malicioso registra a transmissão e a reproduz posteriormente para fazer com que o receptor seja 'desbloqueado'.  

![image](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/12ba0ed7-7ac2-4ef8-9f11-4f047d3efd95)

![image](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/1b11aadc-b63e-49f5-83c3-1102cffc53a2)

Após o código ser enviado e aceito, ele é incrementado.

## Ataque Rolljam
Este ataque se consiste em bloquear e capturar o primeiro código, aguardar o proprietário do carro usar a chave para tentar trancar novamente (ação normal), bloquear e capturar o segundo código e, por fim, retransmitir o primeiro código. 
Como o segundo código ainda não foi usado, ele será válido para trancar ou destrancar o carro na próxima retransmissão.


![image](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/d082402c-704d-4f0b-abd2-17fdbfd17be3)

![image](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/cf7ab569-eee3-44bb-aa61-0f10e4dc467c)

## Dispositivos
Para realizar este ataque, os dispositivos mais usados e conhecidos são:
- HackRF One
- Evil Crow RF V2 (2x - um para bloquear e outro para capturar/transmitir).
- Yard Stick One (para bloquear) e RTL-SDR (para capturar).