---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Log DSC
ms.openlocfilehash: 50fd6cd31ba426108830fcf124a767318060a95d
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268433"
---
# <a name="dsc-log-resource"></a>Risorsa Log DSC

_Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0_

La risorsa __Log__ in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per scrivere messaggi nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> Per impostazione predefinita sono abilitati solo i log operativi per DSC. Per rendere disponibile o visibile il log analitico, è necessario abilitarlo. Per altre informazioni, vedere [Dove sono i registri eventi DSC?](troubleshooting.md#where-are-dsc-event-logs).

## <a name="properties"></a>Proprietà

| Proprietà | Description |
| --- | --- |
| Message| Indica il messaggio che si vuole scrivere nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.|
| DependsOn | Indica che prima di poter scrivere questo messaggio del registro è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = '[ResourceType]ResourceName'`.|

## <a name="example"></a>Esempio

L'esempio seguente mostra come includere un messaggio nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.

> [!NOTE]
> Se si esegue [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) con questa risorsa configurata, il cmdlet restituisce sempre **$false**.

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```