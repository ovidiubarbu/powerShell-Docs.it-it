---
title: Risorsa WindowsProcess DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 7e8c0d39d4f49d09acef79d789ee54f158e465f8
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
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
|  Proprietà  |  Descrizione   | 
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

