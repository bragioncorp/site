---
title: "Como trocar o IP a cada 5 segundos"
excerpt: "Aprenda a trocar seu IP a cada 5 segundos ou mais usando Tor e FoxyProxy."
categories:
  - Hacking
tags:
  - IP
  - Trocar IP
  - Tor
  - Anonimato
  - Proxy
  - Firefox
  - FoxyProxy
  - Kali Linux
  - gr33n37

toc: true
---

# Atenção
Eu não sou o criador original do script. Meu trabalho aqui é apenas oferecer um passo-a-passo da instalação e uso em pt-BR.  
Todos os créditos vão para [gr33n37](https://github.com/gr33n37).  

# Explicação rápida
O script fornece o IP aleatório ao iniciar o Tor e depois de 'n' segundos definido pelo usuário o mesmo serviço é reiniciado, fornecendo um outro IP.

# Passos
## Etapa 1
### Verifique seu IP
Usando o [dnsleaktest](https://dnsleaktest.com/) você pode conferir seu IP público.  

![ip1](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/81d25a86-1ba0-4ac7-a967-f6bae98c15b1)

### Clone o repositório
    git clone https://github.com/gr33n37/gr33n37-ip-changer.git

### Acesse a pasta
    cd gr33n37-ip-changer

### Conceda permissão de execução ao arquivo .sh
    chmod +x ip-changer.sh

### Abra um terminal no modo sudo e execute
    ./ip-changer.sh

## Etapa 2
Ao executar o script, duas perguntas serão feitas:  
- o intervalo para a troca de IPs (em segundos).  
- a quantidade de vezes que o IP será trocado.  

Para facilitar os testes, escolhi 5 e 0, respectivamente.  
O 0 significa que eu aceito a troca infinita de IPs.

Após isso, o script já começa a seu trabalho.  

![ip4](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/2ec7290b-38e0-4014-ade3-57c9755f1611)

## Etapa 3
### Configuração do FoxyProxy
- Abra o seu navegador Firefox.  
- Aperte CTRL + SHIF + A para acessar o página de add-ons.  
- Procure por FoxyProxy.  

![ip5](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/4a82db9e-7850-4d8a-aac4-6e1714fe5e86)

- Abra a extensão e crie um novo proxy.  

![ip7](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/c15f9395-4f5a-4baa-8cae-fb111225f4c1)

> O tipo precisa ser SOCK4.  
> O hostname precisa ser 127.0.0.1 (ou outro endereço de loopback).  
> A porta precisa ser 9050 (ou outra porta específica do seu Tor).  

### Selecionando configuração criada
Por fim, basta abrir o menu do FoxyProxy e escolher o proxy criado.

## Resultados
Aqui estão os meus resultados.  

![ip2](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/cdd48326-5e3c-4817-8097-bf07545b1f9e)

Após 5 segundos...  

![ip3](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/65d9f79e-5359-4540-bb74-2f1072d6104a)

A atribuição do novo IP não é 100% precisa, podendo vaiar menos ou mais tempo.  