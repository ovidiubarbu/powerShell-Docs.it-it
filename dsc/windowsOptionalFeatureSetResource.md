---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsOptionalFeatureSet DSC
ms.openlocfilehash: 7c5eb553b396776f54a36bec8971f71ec61f9354
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>Risorsa WindowsOptionalFeatureSet DSC

> Si applica a: Windows PowerShell 5.0

La risorsa **WindowsOptionalFeatureSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare le funzionalità facoltative abilitate in un nodo di destinazione.
Questa risorsa è una [risorsa composta](authoringResourceComposite.md) che chiama la [risorsa WindowsOptionalFeature](windowsOptionalFeatureResource.md) per ogni funzionalità specificata nella proprietà `Name`.

Usare questa risorsa quando si vogliono configurare diverse istanze di Windows facoltative nello stesso stato.

## <a name="syntax"></a>Sintassi

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Proprietà

|  Proprietà  |  Description   |
|---|---|
| Nome| Indica il nome delle funzionalità che si vogliono abilitare o disabilitare.|
| Ensure| Specifica se le funzionalità sono abilitate. Per specificare che le funzionalità sono abilitate impostare la proprietà su "Enable". Per specificare che le funzionalità sono disabilitate impostare la proprietà su "Disable".|
| Source| Non implementata.|
| NoWindowsUpdateCheck| Specifica se DISM contatta Windows Update (WU) durante la ricerca dei file di origine per abilitare le funzionalità. Se $true, DISM non contatta WU.|
| RemoveFilesOnDisable| Se è impostata su **$true** consente di rimuovere tutti i file associati alle funzionalità quando sono disabilitate (ossia, quando **Ensure** è impostata su "Absent").|
| LogLevel| Livello di output massimo per i log. I valori consentiti sono: "ErrorsOnly" (vengono registrati solo gli errori), "ErrorsAndWarning" (vengono registrati errori e avvisi) e "ErrorsAndWarningAndInformation" (vengono registrati errori, avvisi e informazioni di debug).|
| LogPath| Percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.|
| DependsOn| Specifica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|