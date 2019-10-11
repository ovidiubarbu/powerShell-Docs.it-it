---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WaitForAny DSC
ms.openlocfilehash: 61fee456d2652e08ed9bdbe64457627ff5b2e145
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952998"
---
# <a name="dsc-waitforany-resource"></a>Risorsa WaitForAny DSC

> Si applica a: Windows PowerShell 5.1

La risorsa DSC **WaitForAny** può essere usata all'interno di un blocco del nodo in una [configurazione DSC](../../../configurations/configurations.md) per specificare le dipendenze da configurazioni in altri nodi.

La risorsa ha esito positivo se la risorsa specificata dalla proprietà **ResourceName** è nello stato desiderato in tutti i nodi di destinazione definiti nella proprietà **NodeName**.

> [!NOTE]
> La risorsa **WaitForAny** usa Gestione remota Windows per controllare lo stato degli altri nodi. Per altre informazioni sulla porta e sui requisiti di sicurezza per Gestione remota Windows, vedere [Considerazioni sulla sicurezza della comunicazione remota di PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).

## <a name="syntax"></a>Sintassi

```Syntax
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string[]]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Description |
|---|---|
|NomeRisorsa |Il nome della risorsa da cui dipendere. Se questa risorsa appartiene a una configurazione diversa, formattare il nome come `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`. |
|NodeName |I nodi di destinazione della risorsa da cui dipendere. |
|RetryIntervalSec |Il numero di secondi prima di riprovare. Il valore minimo è 1. |
|RetryCount |Il numero massimo di tentativi. |
|ThrottleLimit |Numero di computer da connettere contemporaneamente. Il valore predefinito è `New-CimSession`. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Esempio

Per un esempio di come usare questa risorsa, vedere [Specifica delle dipendenze tra nodi](../../../configurations/crossNodeDependencies.md)