---
title: Risorsa User DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 5c7878bdfc8a3f118b569a9e43be6c7e4333ad2c

---

#Risorsa User DSC#

 
>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0


La risorsa __User__ in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire gli account utente locali nel nodo di destinazione.


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

## Esempio

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = “[Group]GroupExample" # Configures GroupExample first
}
```




<!--HONumber=Aug16_HO3-->


