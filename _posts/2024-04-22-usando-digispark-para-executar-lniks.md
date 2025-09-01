---
title: "Usando Digispark para Executar Links"
excerpt: "Aprenda a excutar um link ou vários links no computador usando o Arduino Digispark."
categories:
  - Hacking
tags:
  - Digispark
  - Arduino
  - Tor
  - Proxy

toc: true
---

# Explicação rápida
Além de ser possível a montagem e uso do Digispark em uma protoboard, você também pode usá-lo como um HID (Dispositivo de Interface Humana) para executar código na máquina.

![image](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/29015d37-717b-4034-af70-841845dfd336)

Você pode adquirir um no Mercado Livre, AliExpress, Ebay ou qualquer outra loja.

# Instalação
## IDE
Você pode pesquisar Arduino IDE na Microsoft Store e instalar por lá.

## Drivers
Antes de executar qualquer código, é preciso instalar o driver.  
- Acesse [Digistump arduino release](https://github.com/digistump/DigistumpArduino/releases).  
- Faça o download do arquivo "Digistump.Drivers.zip" da versão mais atualizada.
- Após isso, execute o arquivo "DPinst64.exe" e siga os passos.

## URLs Adicionais
Clique em "Arquivo", "Preferências" e no o campo "URLs Adicionais para Gerenciadores de Placa" adicione o seguinte link:

    https://raw.githubusercontent.com/digistump/arduino-boards-index/master/package_digistump_index.json

## Gerenciador de placas
- Vá em "Ferramentas", "Placas", "Gerenciador de Placas" e pesquise por "digistump".  
- Deverá aparecer a opção "Digistump AVR Boards".  
- Selecione a versão mais atualizada e instale.  

> Versão usada durante a postagem: 1.6.7.  

## Selecione a Placa
Selecione a placa Digispark Default.  

# Código
Depois se terminar as instalações, basta criar um projeto Arduino e colar o código.  
Substitua SEU_LINK pelo link de um vídeo, imagem ou gif.  

    #include "DigiKeyboard.h"
    void setup() {
    }

    void loop() {
      DigiKeyboard.sendKeyStroke(0);
      DigiKeyboard.delay(500);
      DigiKeyboard.sendKeyStroke(KEY_R, MOD_GUI_LEFT);
      DigiKeyboard.delay(500);
      DigiKeyboard.print("cmd");
      DigiKeyboard.sendKeyStroke(KEY_ENTER);
      DigiKeyboard.delay(2300);
      DigiKeyboard.print("powershell Start-Process SEU_LINK");
      DigiKeyboard.sendKeyStroke(KEY_ENTER);
      DigiKeyboard.print("exit");
      DigiKeyboard.sendKeyStroke(KEY_ENTER);
      for(;;){ }
    }

Depois de colar o código no seu projeto e clicar em "Carregar", terá 60 segundos para conectar o Digispark em alguma porta USB para que o código seja gravado nele (ele não apresenta porta COM).

# Execução
Ao conectar o Digispark no computador, abrirá o "prompt", executará o comando "powershell Start-Process SEU_LINK" e fechará o "prompt".