---
title: Risorsa Service DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: bda348e6597f31b8dfa2014e5c34c5d3bc7bca15
ms.openlocfilehash: 10123359213df7180388d9251e032c2bbb673143

---

# Risorsa Service DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0


La risorsa **Service** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi nel nodo di destinazione.

## Sintassi

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## Proprietà

|  Proprietà  |  Descrizione   | 
|---|---| 
| Name| Indica il nome del servizio. A volte questo nome è diverso da quello visualizzato. È possibile ottenere un elenco dei servizi e del rispettivo stato corrente usando il cmdlet Get-Service.| 
| BuiltInAccount| Indica l'account di accesso da usare per il servizio. I valori consentiti per questa proprietà sono: **LocalService**, **LocalSystem** e **NetworkService**.| 
| Credential| Indica le credenziali per l'account in cui verrà eseguito il servizio. Questa proprietà e la proprietà __BuiltinAccount__ non possono essere usate insieme.| 
| DependsOn| Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 
| StartupType| Indica il tipo di avvio per il servizio. I valori consentiti per questa proprietà sono: **Automatic**, **Disabled** e **Manual**| 
| State| Indica lo stato che si vuole specificare per il servizio.| 
| Descrizione | Specifica la descrizione del servizio di destinazione.| 
| DisplayName | Indica il nome visualizzato del servizio di destinazione.| 
| Ensure | Indica se il servizio di destinazione è presente nel sistema. Impostare questa proprietà su **Absent** per specificare che il servizio di destinazione non esiste. Se la proprietà è impostata su **Present** (valore predefinito), specifica che il servizio di destinazione esiste.|
| Path | Indica il percorso del file binario per un nuovo servizio.| 

## Esempio

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```




<!--HONumber=Jul16_HO1-->


