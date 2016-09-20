---
title: Risorsa Log DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 62f993e3d3e6ef744fb07920d332d476dfd24fc6
ms.openlocfilehash: 60085295fa7df6179a81cd98859cd33e6923150f

---

# Risorsa Log DSC 

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa __Log__ in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per scrivere messaggi nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

NOTA: per impostazione predefinita sono abilitati solo i log operativi per DSC.
Per rendere disponibile o visibile il log analitico, è necessario abilitarlo.
Vedere l'articolo seguente.

[Dove sono i log eventi DSC?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## Proprietà
|  Proprietà  |  Descrizione   | 
|---|---| 
| Message| Indica il messaggio che si vuole scrivere nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.| 
| DependsOn | Indica che prima di poter scrivere questo messaggio del registro è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 

## Esempio

L'esempio seguente mostra come includere un messaggio nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.

> **Nota**: se si esegue [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) con questa risorsa configurata, il cmdlet restituisce sempre **$false**.

```powershell 
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```




<!--HONumber=Sep16_HO3-->


