---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa ProcessSet DSC
ms.openlocfilehash: 412cf1076996126f0d9b7a9a8ebbc9bdb7ecf377
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-windowsprocess-resource"></a>Risorsa WindowsProcess DSC

> Si applica a: Windows PowerShell 5.0

La risorsa **ProcessSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per configurare i processi in un nodo di destinazione. Questa risorsa è una [risorsa composta](authoringResourceComposite.md) che chiama la [risorsa WindowsProcess](windowsProcessResource.md) per ogni gruppo specificato nel parametro `GroupName`.

## <a name="syntax"></a>Sintassi

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Proprietà
|  Proprietà  |  Description   |
|---|---|
| Arguments| Stringa che contiene argomenti da passare al processo così come è. Se è necessario passare più argomenti, inserirli tutti in questa stringa.|
| Path| Percorsi degli eseguibili del processo. Se questi sono i nomi dei file eseguibili (non i percorsi completi), la risorsa DSC cercherà i file nella variabile **Path** di ambiente (`$env:Path`). Se i valori di questa proprietà sono percorsi completi, DSC non userà la variabile **Path** di ambiente per individuare i file e genererà un errore se il percorso non esiste. I percorsi relativi non sono consentiti.|
| Credential| Indica le credenziali per l'avvio del processo.|
| Ensure| Specifica se il processo esiste. Impostare questa proprietà su "Present" per specificare che il processo esiste. In caso contrario, impostarla su "Absent". Il valore predefinito è "Present".|
| StandardErrorPath| Percorso in cui i processi scrivono l'errore standard. Qualsiasi file esistente verrà sovrascritto.|
| StandardInputPath| Flusso da cui il processo riceve l'input standard.|
| StandardOutputPath| Percorso del file in cui i processi scrivono l'output standard. Qualsiasi file esistente verrà sovrascritto.|
| WorkingDirectory| Percorso usato come directory di lavoro corrente per i processi.|
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **_ResourceType**, la sintassi per usare questa proprietà è 'DependsOn = "[ResourceType]ResourceName"''.|