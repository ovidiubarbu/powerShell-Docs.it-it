---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Risorsa Group DSC
ms.openlocfilehash: 6fb6c5f9593687d7204ff31fddd9bca978ed2707
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="dsc-group-resource" class="xliff"></a>
# Risorsa Group DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa Group in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i gruppi locali nel nodo di destinazione.

<a id="syntax" class="xliff"></a>
## Sintassi
```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

<a id="properties" class="xliff"></a>
## Proprietà

|  Proprietà  |  Descrizione   | 
|---|---| 
| GroupName| Il nome del gruppo per cui si vuole specificare un determinato stato.| 
| Credential| Le credenziali necessarie per accedere a risorse remote. **Nota**: per aggiungere tutti gli account non locali al gruppo, questo account deve avere le autorizzazioni di Active Directory appropriate. In caso contrario, quando la configurazione viene eseguita nel nodo di destinazione, si verifica un errore.  
| Descrizione| La descrizione dell'attività.| 
| Ensure| Indica se il gruppo esiste. Impostare questa proprietà su "Absent" per specificare che il gruppo non esiste. Se la proprietà è impostata su "Present" (valore predefinito), specifica che il gruppo esiste.| 
| Membri| Usare questa proprietà per sostituire l'appartenenza al gruppo corrente con i membri specificati. Il valore di questa proprietà è una matrice di stringhe del formato *Dominio*\\*Nome utente*. Se si imposta questa proprietà in una configurazione, non usare la proprietà **MembersToExclude** o **MembersToInclude**. Questa operazione genera un errore.| 
| MembersToExclude| Usare questa proprietà per rimuovere membri dall'appartenenza al gruppo esistente. Il valore di questa proprietà è una matrice di stringhe del formato *Dominio*\\*Nome utente*. Se si imposta questa proprietà in una configurazione, non usare la proprietà **Members**. Questa operazione genera un errore.| 
| MembersToInclude| Usare questa proprietà per aggiungere membri all'appartenenza al gruppo esistente. Il valore di questa proprietà è una matrice di stringhe del formato *Dominio*\\*Nome utente*. Se si imposta questa proprietà in una configurazione, non usare la proprietà **Members**. In caso contrario, verrà generato un errore.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"``.| 

<a id="example-1" class="xliff"></a>
## Esempio 1

L'esempio seguente illustra come specificare che un gruppo denominato "TestGroup" sia assente. 

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
<a id="example-2" class="xliff"></a>
## Esempio 2
L'esempio seguente illustra come aggiungere un utente Active Directory al gruppo Administrators locale come parte della compilazione di un ambiente con più computer in cui è già in uso un PSCredential per l'account amministratore locale. Questo utente viene anche usato per l'account amministratore di dominio (dopo l'innalzamento di livello di un dominio). A questo punto è necessario convertire il PSCredential esistente in credenziali descrittive del dominio per consentire l'aggiunta di un utente di dominio al gruppo Administrators locale del server membro.

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
     @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'   
      }    
    )
}
                  
$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup
        {
            GroupName='Administrators'   
            Ensure= 'Present'             
            MembersToInclude= "$domain\$($Node.AdminAccount)"
            Credential = $dCredential    
            PsDscRunAsCredential = $DCredential
        }
```

<a id="example-3" class="xliff"></a>
## Esempio 3
L'esempio seguente illustra come garantire che un gruppo locale, TigerTeamAdmins, nel server TigerTeamSource.Contoso.Com non contenga un account di dominio specifico, Contoso\JerryG.  

```powershell

Configuration SecureTigerTeamSrouce 
{
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'
  
  Node TigerTeamSource.Contoso.Com {
  Group TigerTeamAdmins
    {
       GroupName        = 'TigerTeamAdmins'   
       Ensure           = 'Absent'             
       MembersToInclude = "Contoso\JerryG"
    }
  }
}
```

