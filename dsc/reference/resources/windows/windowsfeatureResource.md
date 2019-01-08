---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsFeature DSC
ms.openlocfilehash: 7a57f4b2797ab3bb202aea8b2543d1e3f14074e9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047695"
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