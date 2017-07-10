---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WaitForSome DSC
ms.openlocfilehash: 5d67a9111f6358240590b651e627ffb96abc0896
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="dsc-waitforsome-resource" class="xliff"></a>
# Risorsa WaitForSome DSC

> Si applica a: Windows PowerShell 5.0 e versioni successive

La risorsa DSC **WaitForAny** può essere usata all'interno di un blocco del nodo in una [configurazione DSC](configurations.md) per specificare le dipendenze da configurazioni in altri nodi.

La risorsa ha esito positivo se la risorsa specificata dalla proprietà **ResourceName** si trova nello stato desiderato in un numero minimo di nodi, specificato in **NodeCount**, definito dalla proprietà **NodeName**. 


<a id="syntax" class="xliff"></a>
## Sintassi

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    NodeCount = [Uint32]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

<a id="properties" class="xliff"></a>
## Proprietà

|  Proprietà  |  Descrizione   | 
|---|---| 
| NomeRisorsa| Il nome della risorsa da cui dipendere.| 
| NodeName| I nodi di destinazione della risorsa da cui dipendere.| 
| NodeCount| Il numero minimo di nodi che devono essere nello stato desiderato perché la risorsa abbia esito positivo.|
| RetryIntervalSec| Il numero di secondi prima di riprovare. Il valore minimo è 1.| 
| RetryCount| Il numero massimo di tentativi.| 
| ThrottleLimit| Numero di computer da connettere contemporaneamente. Il valore predefinito è new-cimsession.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|


<a id="example" class="xliff"></a>
## Esempio

Per un esempio di come usare questa risorsa, vedere [Specifica delle dipendenze tra nodi](crossNodeDependencies.md)

