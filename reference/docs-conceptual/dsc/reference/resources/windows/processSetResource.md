---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa ProcessSet DSC
ms.openlocfilehash: 72925d3a9516f5c0040427773a3b1d66034667bb
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953128"
---
# <a name="dsc-processset-resource"></a>Risorsa ProcessSet DSC

> Si applica a: Windows PowerShell 5.x

La risorsa **ProcessSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per configurare i processi in un nodo di destinazione.

## <a name="syntax"></a>Sintassi

```Syntax
ProcessSet [string] #ResourceName
{
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Description |
|---|---|
|Path |Percorso dell'eseguibile del processo. Se questi sono i nomi dei file eseguibili (non i percorsi completi), la risorsa DSC cercherà i file nella variabile `$env:Path` di ambiente. Se i valori di questa proprietà sono percorsi completi, DSC non userà la variabile `$env:Path` di ambiente per individuare i file e genererà un errore in presenza di percorsi non esistenti. I percorsi relativi non sono consentiti. |
|Credential |Indica le credenziali per l'avvio del processo. |
|StandardErrorPath |Percorso in cui i processi scrivono l'errore standard. Qualsiasi file esistente verrà sovrascritto. |
|StandardInputPath |Flusso da cui il processo riceve l'input standard. |
|StandardOutputPath |Percorso del file in cui i processi scrivono l'output standard. Qualsiasi file esistente verrà sovrascritto. |
|WorkingDirectory |Percorso usato come directory di lavoro corrente per i processi. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Specifica se il processo esiste. Impostare questa proprietà su **Present** per specificare che il processo esiste. In caso contrario, impostarla su **Absent**. Il valore predefinito è **Present**. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).