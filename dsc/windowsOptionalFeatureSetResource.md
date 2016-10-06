---
title: Risorsa WindowsOptionalFeatureSet DSC
ms.date: 2016-05-24
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 97714d3fa9a1c00fb3d2e79cc873280ca945a840
ms.openlocfilehash: 52eb958e59ecb1d5ae3faf268933bbd544410d47

---

# Risorsa WindowsOptionalFeatureSet DSC

> Si applica a: Windows PowerShell 5.0

La risorsa **WindowsOptionalFeatureSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare le funzionalità facoltative abilitate in un nodo di destinazione. Questa risorsa è una [risorsa composta](authoringResourceComposite.md) che chiama la [risorsa WindowsOptionalFeature](windowsOptionalFeatureResource.md) per ogni funzionalità specificata nella proprietà `Name`.

Usare questa risorsa quando si vogliono configurare diverse istanze di Windows facoltative nello stesso stato.

## Sintassi

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ] 
    [ RemoveFilesOnDisable = [bool] ]  
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    
}
```

## Proprietà

|  Proprietà  |  Descrizione   | 
|---|---| 
| Name| Indica il nome delle funzionalità che si vogliono abilitare o disabilitare.| 
| Ensure| Specifica se le funzionalità sono abilitate. Per specificare che le funzionalità siano abilitate, impostare questa proprietà su "Present". Per specificare che le funzionalità siano disabilitate, impostare la proprietà su "Absent".|
| Source| Non implementata.|
| NoWindowsUpdateCheck| Specifica se DISM contatta Windows Update (WU) durante la ricerca dei file di origine per abilitare le funzionalità. Se $true, DISM non contatta WU.|
| RemoveFilesOnDisable| Se è impostata su **$true** consente di rimuovere tutti i file associati alle funzionalità quando sono disabilitate (ossia, quando **Ensure** è impostata su "Absent").|
| LogLevel| Livello di output massimo per i log. I valori consentiti sono: "ErrorsOnly" (vengono registrati solo gli errori), "ErrorsAndWarning" (vengono registrati errori e avvisi) e "ErrorsAndWarningAndInformation" (vengono registrati errori, avvisi e informazioni di debug).|
| LogPath| Percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.| 
| DependsOn| Specifica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 
 






<!--HONumber=Aug16_HO3-->


