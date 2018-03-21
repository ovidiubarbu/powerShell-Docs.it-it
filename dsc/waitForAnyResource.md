---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WaitForAny DSC
ms.openlocfilehash: 43922dbcccb6d06d7d9edfcf16ce4eb107e9d4e6
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-waitforany-resource"></a>Risorsa WaitForAny DSC

> Si applica a: Windows PowerShell 5.1 e versioni successive

La risorsa DSC **WaitForSome** può essere usata all'interno di un blocco del nodo in una [configurazione DSC](configurations.md) per specificare le dipendenze da configurazioni in altri nodi.

La risorsa ha esito positivo se la risorsa specificata dalla proprietà **ResourceName** è nello stato desiderato in qualsiasi nodo di destinazione definito nella proprietà **NodeName**.


## <a name="syntax"></a>Sintassi

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Proprietà

|  Proprietà  |  Description   | 
|---|---| 
| NomeRisorsa| Il nome della risorsa da cui dipendere. Se questa risorsa appartiene a un'altra configurazione, il formato del nome deve essere "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]: [ __ConfigurationName__] "| 
| NodeName| I nodi di destinazione della risorsa da cui dipendere.| 
| RetryIntervalSec| Il numero di secondi prima di riprovare. Il valore minimo è 1.| 
| RetryCount| Il numero massimo di tentativi.| 
| ThrottleLimit| Numero di computer da connettere contemporaneamente. Il valore predefinito è new-cimsession.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Esempio

Per un esempio di come usare questa risorsa, vedere [Specifica delle dipendenze tra nodi](crossNodeDependencies.md)

