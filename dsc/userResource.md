---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa User DSC
ms.openlocfilehash: a4e4e8af4fcfe5c997c460613174d8583261dedf
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="dsc-user-resource" class="xliff"></a>
#Risorsa User DSC#

 
>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0


La risorsa __User__ in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire gli account utente locali nel nodo di destinazione.


<a id="syntax" class="xliff"></a>
##Sintassi##

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

<a id="properties" class="xliff"></a>
## Proprietà
|  Proprietà  |  Descrizione   | 
|---|---| 
| UserName| Indica il nome dell'account per cui si vuole specificare un determinato stato.| 
| Descrizione| Indica la descrizione che si vuole usare per l'account utente.| 
| Disabled| Indica se l'account è abilitato. Impostare questa proprietà su __$true__ per specificare che l'account è disabilitato e su __$false__ per specificare che è abilitato.| 
| Ensure| Indica se l'account esiste. Impostare questa proprietà su "Present" per specificare che l'account esiste e su "Absent" per specificare che non esiste.| 
| FullName| Rappresenta una stringa che contiene il nome completo da usare per l'account utente.| 
| Password| Indica la password da usare per l'account. | 
| PasswordChangeNotAllowed| Indica se l'utente può modificare la password. Impostare questa proprietà su __$true__ per impedire all'utente di modificare la password e su __$false__ per consentire all'utente di modificare la password. Il valore predefinito è __$false__.| 
| PasswordChangeRequired| Indica se l'utente dovrà cambiare la password all'accesso successivo. Impostare questa proprietà su __$true__ se l'utente deve cambiare la password. Il valore predefinito è __$true__.| 
| PasswordNeverExpires| Indica se la password scadrà. Impostare questa proprietà su __$true__ per specificare che la password per questo utente non scade mai e su __$false__ se la password scade. Il valore predefinito è __$false__.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 

<a id="example" class="xliff"></a>
## Esempio

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```

