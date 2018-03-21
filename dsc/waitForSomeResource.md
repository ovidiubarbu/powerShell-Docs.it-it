---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WaitForSome DSC
ms.openlocfilehash: 8b0ad0dbd31816cc673c7f77945927987e90e08b
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-waitforsome-resource"></a>Risorsa WaitForSome DSC

> Si applica a: Windows PowerShell 5.0 e versioni successive

La risorsa DSC **WaitForAny** può essere usata all'interno di un blocco del nodo in una [configurazione DSC](configurations.md) per specificare le dipendenze da configurazioni in altri nodi.

La risorsa ha esito positivo se la risorsa specificata dalla proprietà **ResourceName** si trova nello stato desiderato in un numero minimo di nodi, specificato in **NodeCount**, definito dalla proprietà **NodeName**. 


## <a name="syntax"></a>Sintassi

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a>Proprietà

|  Proprietà  |  Description   | 
|---|---| 
| NodeCount| Il numero minimo di nodi che devono essere nello stato desiderato perché la risorsa abbia esito positivo.|
| NodeName| I nodi di destinazione della risorsa da cui dipendere.| 
| NomeRisorsa| Il nome della risorsa da cui dipendere. Se questa risorsa appartiene a un'altra configurazione, il formato del nome deve essere "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]: [ __ConfigurationName__] "| 
| RetryIntervalSec| Il numero di secondi prima di riprovare. Il valore minimo è 1.| 
| RetryCount| Il numero massimo di tentativi.| 
| ThrottleLimit| Numero di computer da connettere contemporaneamente. Il valore predefinito è new-cimsession.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|
| PsDscRunAsCredential | Vedere [Esecuzione di DSC con le credenziali dell'utente](https://docs.microsoft.com/powershell/dsc/runasuser) |


## <a name="example"></a>Esempio

Per un esempio di come usare questa risorsa, vedere [Specifica delle dipendenze tra nodi](crossNodeDependencies.md)

