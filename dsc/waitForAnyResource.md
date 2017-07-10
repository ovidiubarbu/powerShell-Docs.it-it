---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Risorsa WaitForAny DSC
ms.openlocfilehash: ba1873cc0ecfc4596cbad5b61b4a52b61ea4778a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="dsc-waitforany-resource" class="xliff"></a>
# Risorsa WaitForAny DSC

> Si applica a: Windows PowerShell 5.1 e versioni successive

La risorsa DSC **WaitForSome** può essere usata all'interno di un blocco del nodo in una [configurazione DSC](configurations.md) per specificare le dipendenze da configurazioni in altri nodi.

La risorsa ha esito positivo se la risorsa specificata dalla proprietà **ResourceName** è nello stato desiderato in qualsiasi nodo di destinazione definito nella proprietà **NodeName**.


<a id="syntax" class="xliff"></a>
## Sintassi

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

<a id="properties" class="xliff"></a>
## Proprietà

|  Proprietà  |  Descrizione   | 
|---|---| 
| NomeRisorsa| Il nome della risorsa da cui dipendere.| 
| NodeName| I nodi di destinazione della risorsa da cui dipendere.| 
| RetryIntervalSec| Il numero di secondi prima di riprovare. Il valore minimo è 1.| 
| RetryCount| Il numero massimo di tentativi.| 
| ThrottleLimit| Numero di computer da connettere contemporaneamente. Il valore predefinito è new-cimsession.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|


<a id="example" class="xliff"></a>
## Esempio

Per un esempio di come usare questa risorsa, vedere [Specifica delle dipendenze tra nodi](crossNodeDependencies.md)

