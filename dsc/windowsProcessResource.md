---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsProcess DSC
ms.openlocfilehash: ec77209637d574a0e530f4cce283e1ad98701cdb
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsprocess-resource"></a>Risorsa WindowsProcess DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa **WindowsProcess** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per configurare i processi in un nodo di destinazione.

## <a name="syntax"></a>Sintassi

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a>Proprietà
|  Proprietà  |  Description   | 
|---|---| 
| Arguments| Indica una stringa di argomenti da passare al processo come è. Se è necessario passare più argomenti, inserirli tutti in questa stringa.| 
| Path| Percorso dell'eseguibile del processo. Se è il nome del file eseguibile (non il percorso completo), la risorsa DSC cercherà il file eseguibile nella variabile **Path** di ambiente (`$env:Path`). Se il valore di questa proprietà è un percorso completo, DSC non userà la variabile **Path** di ambiente per individuare il file e genererà un errore se il percorso non esiste. I percorsi relativi non sono consentiti.| 
| Credential| Indica le credenziali per l'avvio del processo.| 
| Ensure| Indica se il processo esiste. Impostare questa proprietà su "Present" per specificare che il processo esiste. In caso contrario, impostarla su "Absent". Il valore predefinito è "Present".| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"``.| 
| StandardErrorPath| Indica il percorso della directory in cui scrivere l'errore standard. Qualsiasi file esistente verrà sovrascritto.| 
| StandardInputPath| Indica il percorso di input standard.| 
| StandardOutputPath| Indica il percorso in cui scrivere l'output standard. Qualsiasi file esistente verrà sovrascritto.| 
| WorkingDirectory| Indica il percorso che verrà usato come directory di lavoro corrente per il processo.| 

