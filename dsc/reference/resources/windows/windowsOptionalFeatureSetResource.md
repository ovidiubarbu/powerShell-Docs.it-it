---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsOptionalFeatureSet DSC
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047615"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>Risorsa WindowsOptionalFeatureSet DSC

> Si applica a: Windows PowerShell 5.0

La risorsa **WindowsOptionalFeatureSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare le funzionalità facoltative abilitate in un nodo di destinazione.
Questa risorsa è una [risorsa composta](../../../resources/authoringResourceComposite.md) che chiama la [risorsa WindowsOptionalFeature](windowsOptionalFeatureResource.md) per ogni funzionalità specificata nella proprietà `Name`.

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
| LogLevel| Livello di output massimo per i log. I valori accettati sono: "ErrorsOnly" (vengono registrati solo gli errori), "ErrorsAndWarning" (errori e avvisi vengono registrati) e "ErrorsAndWarningAndInformation" (vengono registrati errori, avvisi e informazioni di debug).|
| LogPath| Percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.|
| DependsOn| Specifica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|
