---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WaitForAll DSC
ms.openlocfilehash: 1e891f1aecbdbe641973669f71f22664ad8ea16c
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047656"
---
# <a name="dsc-waitforall-resource"></a>Risorsa WaitForAll DSC

> Si applica a: Windows PowerShell 5.0 e versioni successive

La risorsa DSC **WaitForAll** può essere usata all'interno di un blocco del nodo in una [configurazione DSC](../../../configurations/configurations.md) per specificare le dipendenze da configurazioni in altri nodi.

La risorsa ha esito positivo se la risorsa specificata dalla proprietà **ResourceName** è nello stato desiderato in tutti i nodi di destinazione definiti nella proprietà **NodeName**.

## <a name="syntax"></a>Sintassi

```
WaitForAll [string] #ResourceName
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

Per un esempio di come usare questa risorsa, vedere [Specifica delle dipendenze tra nodi](../../../configurations/crossNodeDependencies.md)
