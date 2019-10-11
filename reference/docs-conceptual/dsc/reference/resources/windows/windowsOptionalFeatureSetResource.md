---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsOptionalFeatureSet DSC
ms.openlocfilehash: f378006a6c362ee9890d70dd76fb552dd262a544
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952868"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>Risorsa WindowsOptionalFeatureSet DSC

> Si applica a: Windows PowerShell 5.x

La risorsa **WindowsOptionalFeatureSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare le funzionalità facoltative abilitate in un nodo di destinazione. Questa risorsa è una [risorsa composita](../../../resources/authoringResourceComposite.md) che chiama la [risorsa WindowsOptionalFeature](windowsOptionalFeatureResource.md) per ogni funzionalità specificata nella proprietà **Name**.

Usare questa risorsa quando si vogliono configurare diverse istanze di Windows facoltative nello stesso stato.

## <a name="syntax"></a>Sintassi

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Description |
|---|---|
|Nome |Indica il nome delle funzionalità che si vogliono abilitare o disabilitare. |
|Source |Non implementata. |
|NoWindowsUpdateCheck |Specifica se DISM contatta Windows Update (WU) durante la ricerca dei file di origine per abilitare le funzionalità. Se `$true`, DISM non contatta WU. |
|RemoveFilesOnDisable |Impostare su `$true` per rimuovere tutti i file associati alle funzionalità quando **Ensure** è impostata su **Absent**. |
|LogLevel |Livello di output massimo per i log. I valori accettati sono: **ErrorsOnly**, **ErrorsAndWarning** e **ErrorsAndWarningAndInformation**. |
|LogPath |Percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Specifica se le funzionalità sono abilitate. Per assicurarsi che le funzionalità siano abilitate, impostare questa proprietà su **Enable**. Per assicurarsi che le funzionalità siano disabilitate, impostare la proprietà su **Disable**. Il valore predefinito è **Enable**. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).