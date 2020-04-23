---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsOptionalFeature DSC
ms.openlocfilehash: 7312edcaeb47427bf4736f466a9ed41bd7c31f6a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954648"
---
# <a name="dsc-windowsoptionalfeature-resource"></a>Risorsa WindowsOptionalFeature DSC

> Si applica a: Windows PowerShell 5.x

La risorsa **WindowsOptionalFeature** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare le funzionalità facoltative abilitate in un nodo di destinazione.

## <a name="syntax"></a>Sintassi

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Source = [string[]] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Descrizione |
|---|---|
|Nome |Indica il nome della funzionalità che si vuole abilitare o disabilitare. |
|Source (Sorgente) |Non implementato. |
|NoWindowsUpdateCheck |Specifica se DISM contatta Windows Update (WU) durante la ricerca dei file di origine per abilitare una funzionalità. Se `$true`, DISM non contatta WU. |
|RemoveFilesOnDisable |Impostare su `$true` per rimuovere tutti i file associati alla funzionalità quando **Ensure** è impostata su **Absent**. |
|LogLevel |Livello di output massimo per i log. I valori accettati sono: **ErrorsOnly**, **ErrorsAndWarning** e **ErrorsAndWarningAndInformation**. |
|LogPath |Percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Descrizione |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica se la funzionalità è abilitata. Per assicurarsi che la funzionalità sia abilitata, impostare questa proprietà su _Enable_. Per assicurarsi che la funzionalità sia disabilitata, impostare questa proprietà su _Disable_. Il valore predefinito è _Enable_. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).