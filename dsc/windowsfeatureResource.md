---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsFeature DSC
ms.openlocfilehash: 3dd4a9c6f11b0c76054ca3e95796cab8e709a7c6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsfeature-resource"></a>Risorsa WindowsFeature DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa **WindowsFeature** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare che funzionalità e ruoli vengano aggiunti o rimossi in un nodo di destinazione.

## <a name="syntax"></a>Sintassi

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a>Proprietà

|  Proprietà  |  Description   | 
|---|---| 
| Nome| Indica il nome del ruolo o della funzionalità che si vuole aggiungere o rimuovere. Corrisponde alla proprietà __Name__ del cmdlet [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) e non al nome visualizzato del ruolo o della funzionalità.| 
| Credential| Indica le credenziali da usare per aggiungere o rimuovere il ruolo o la funzionalità.| 
| Ensure| Indica se la funzionalità o il ruolo viene aggiunto. Per specificare che la funzionalità o il ruolo deve essere aggiunto, impostare questa proprietà su "Present". Per specificare che la funzionalità o il ruolo venga rimosso, impostare la proprietà su "Absent".| 
| IncludeAllSubFeature| Impostare questa proprietà su __$true__ per specificare lo stato di tutte le funzionalità secondarie necessarie insieme allo stato della funzionalità specificata con la proprietà __Name__.| 
| LogPath| Indica il percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.| 
| DependsOn| Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 
| Source| Indica il percorso del file di origine da usare per l'installazione, se necessario.| 

## <a name="example"></a>Esempio
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```

