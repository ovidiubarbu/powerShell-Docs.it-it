---
title: Risorsa ServiceSet DSC
ms.date: 2016-05-23
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 12438bc9c6e4211b6a31550fa25334a20fde6846
ms.openlocfilehash: 871d697626a0376e8f1f27bdbbf16d8612a56a79

---

# Risorsa ServiceSet DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0


La risorsa **ServiceSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi nel nodo di destinazione. Questa risorsa è una [risorsa composta](authoringResourceComposite.md) che chiama la [risorsa Service](serviceResource.md) per ogni servizio specificato nella proprietà `Name`.

Usare questa risorsa quando si vogliono configurare diversi servizi nello stesso stato.

## Sintassi

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    
}
```

## Proprietà

|  Proprietà  |  Descrizione   | 
|---|---| 
| Name| Indica i nomi del servizio. A volte questo nome è diverso da quelli visualizzati. È possibile ottenere un elenco dei servizi e del rispettivo stato corrente usando il cmdlet [Get-Service](https://technet.microsoft.com/en-us/library/hh849804.aspx).|
| StartupType| Indica il tipo di avvio per il servizio. I valori consentiti per questa proprietà sono: **Automatic**, **Disabled** e **Manual**|  
| BuiltInAccount| Indica l'account di accesso da usare per il servizio. I valori consentiti per questa proprietà sono: **LocalService**, **LocalSystem** e **NetworkService**.| 
| State| Indica lo stato che si vuole specificare per i servizi: **Stopped** o **Running**.| 
| Ensure| Indica se i servizi sono presenti nel sistema. Impostare questa proprietà su **Absent** per specificare che i servizi non esistono. Se la proprietà è impostata su **Present** (valore predefinito), specifica che i servizio di destinazione esistono.|
| Credential| Indica le credenziali per l'account in cui verrà eseguita la risorsa del servizio. Questa proprietà e la proprietà **BuiltinAccount** non possono essere usate insieme.| 
| DependsOn| Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è *ResourceName* e il tipo è *ResourceType*, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 



## Esempio

La configurazione seguente avvia i servizi "Servizi Desktop remoto" e "Audio di Windows".

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```




<!--HONumber=Aug16_HO3-->


