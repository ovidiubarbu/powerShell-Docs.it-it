---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsProcess DSC
ms.openlocfilehash: e168cdebb04f7ec83b73a537a5f188299f40d8b7
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952838"
---
# <a name="dsc-windowsprocess-resource"></a>Risorsa WindowsProcess DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x

La risorsa **WindowsProcess** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per configurare i processi in un nodo di destinazione.

## <a name="syntax"></a>Sintassi

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Description |
|---|---|
|Arguments |Indica una stringa di argomenti da passare al processo come è. Se è necessario passare più argomenti, inserirli tutti in questa stringa. |
|Path |Percorso dell'eseguibile del processo. Se è il nome del file eseguibile (non il percorso completo), la risorsa DSC cercherà il file eseguibile nella variabile `$env:Path` di ambiente. Se il valore di questa proprietà è un percorso completo, DSC non userà la variabile `$env:Path` per individuare il file e genererà un errore se il percorso non esiste. I percorsi relativi non sono consentiti. |
|Credential |Indica le credenziali per l'avvio del processo. |
|StandardErrorPath |Indica il percorso della directory in cui scrivere l'errore standard. Qualsiasi file esistente verrà sovrascritto. |
|StandardInputPath |Indica il percorso di input standard. |
|StandardOutputPath |Indica il percorso in cui scrivere l'output standard. Qualsiasi file esistente verrà sovrascritto. |
|WorkingDirectory |Indica il percorso che verrà usato come directory di lavoro corrente per il processo. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica se il processo esiste. Impostare questa proprietà su **Present** per specificare che il processo esiste. In caso contrario, impostarla su **Absent**. Il valore predefinito è **Present**. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |