---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa ProcessSet DSC
ms.openlocfilehash: 91a2d5b562864addcb8e11062916d291448bbf57
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077110"
---
# <a name="dsc-windowsprocess-resource"></a>Risorsa WindowsProcess DSC

_Si applica a: Windows PowerShell 5.0_

La risorsa **ProcessSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per configurare i processi in un nodo di destinazione. Questa risorsa è una [risorsa composta](../../../resources/authoringResourceComposite.md) che chiama la [risorsa WindowsProcess](windowsProcessResource.md) per ogni gruppo specificato nel parametro `GroupName`.

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

| Proprietà | Description |
| --- | --- |
| Arguments| Stringa che contiene argomenti da passare al processo così come è. Se è necessario passare più argomenti, inserirli tutti in questa stringa.|
| Path| Percorsi degli eseguibili del processo. Se questi sono i nomi dei file eseguibili (non i percorsi completi), la risorsa DSC cercherà i file nella variabile **Path** di ambiente (`$env:Path`). Se i valori di questa proprietà sono percorsi completi, DSC non userà la variabile **Path** di ambiente per individuare i file e genererà un errore se il percorso non esiste. I percorsi relativi non sono consentiti.|
| Credential| Indica le credenziali per l'avvio del processo.|
| Ensure| Specifica se il processo esiste. Impostare questa proprietà su "Present" per specificare che il processo esiste. In caso contrario, impostarla su "Absent". Il valore predefinito è "Present".|
| StandardErrorPath| Percorso in cui i processi scrivono l'errore standard. Qualsiasi file esistente verrà sovrascritto.|
| StandardInputPath| Flusso da cui il processo riceve l'input standard.|
| StandardOutputPath| Percorso del file in cui i processi scrivono l'output standard. Qualsiasi file esistente verrà sovrascritto.|
| WorkingDirectory| Percorso usato come directory di lavoro corrente per i processi.|
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **_ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|
