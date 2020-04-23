---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Log DSC
ms.openlocfilehash: 0a2f12793357fdf10bd4a2f6003f9dc2276b173c
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "75870762"
---
# <a name="dsc-log-resource"></a>Risorsa Log DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x

La risorsa **Log** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per scrivere messaggi nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.

## <a name="syntax"></a>Sintassi

```Syntax
Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> Per impostazione predefinita sono abilitati solo i log operativi per DSC. Per rendere disponibile o visibile il log analitico, è necessario abilitarlo. Per altre informazioni, vedere [Dove sono i registri eventi DSC?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).

## <a name="properties"></a>Proprietà

| Proprietà |                                                   Descrizione                                                    |
| -------- | ---------------------------------------------------------------------------------------------------------------- |
| Message  | Indica il messaggio che si vuole scrivere nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic. |

## <a name="common-properties"></a>Proprietà comuni

|       Proprietà       |                                                                                                                                                          Descrizione                                                                                                                                                           |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| DependsOn            | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
| PsDscRunAsCredential | Imposta le credenziali per l'esecuzione dell'intera risorsa.                                                                                                                                                                                                                                                                        |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra come includere un messaggio nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.

> [!NOTE]
> Se si esegue [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/test-dscconfiguration?view=powershell-5.1) con questa risorsa configurata, il cmdlet restituisce sempre **$false**.

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
