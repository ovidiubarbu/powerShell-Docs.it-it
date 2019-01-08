---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsOptionalFeature DSC
ms.openlocfilehash: 390caefd2ad190afc651b22ed1beb5cf1d604527
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047671"
---
# <a name="dsc-windowsoptionalfeature-resource"></a>Risorsa WindowsOptionalFeature DSC

> Si applica a: Windows PowerShell 5.0

La risorsa **WindowsOptionalFeature** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare le funzionalità facoltative abilitate in un nodo di destinazione.

## <a name="syntax"></a>Sintassi

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Proprietà

|  Proprietà  |  Description   |
|---|---|
| Nome| Indica il nome della funzionalità che si vuole abilitare o disabilitare.|
| Ensure| Specifica se la funzionalità è abilitata. Per specificare che la funzionalità è abilitata impostare la proprietà su "Enable". Per specificare che la funzionalità è disabilitata impostare la proprietà su "Disable".|
| Source| Non implementata.|
| NoWindowsUpdateCheck| Specifica se DISM contatta Windows Update (WU) durante la ricerca dei file di origine per abilitare una funzionalità. Se $true, DISM non contatta WU.|
| RemoveFilesOnDisable| Se è impostata su **$true** consente di rimuovere tutti i file associati alla funzionalità quando è disabilitata (ossia, quando **Ensure** è impostata su "Absent").|
| LogLevel| Livello di output massimo per i log. I valori accettati sono: "ErrorsOnly" (vengono registrati solo gli errori), "ErrorsAndWarning" (errori e avvisi vengono registrati) e "ErrorsAndWarningAndInformation" (vengono registrati errori, avvisi e informazioni di debug).|
| LogPath| Percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.|
| DependsOn| Specifica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|