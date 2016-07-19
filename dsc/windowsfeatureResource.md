---
title: Risorsa WindowsFeature DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 522dbea958a60f76e98abe32e11e6491ea6d457c

---

# Risorsa WindowsFeature DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa **WindowsFeature** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare che funzionalità e ruoli vengano aggiunti o rimossi in un nodo di destinazione.

## Sintassi

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

## Proprietà

|  Proprietà  |  Descrizione   | 
|---|---| 
| Name| Indica il nome del ruolo o della funzionalità che si vuole aggiungere o rimuovere. Corrisponde alla proprietà __Name__ del cmdlet [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) e non al nome visualizzato del ruolo o della funzionalità.| 
| Credential| Indica le credenziali da usare per aggiungere o rimuovere il ruolo o la funzionalità.| 
| Ensure| Indica se la funzionalità o il ruolo viene aggiunto. Per specificare che la funzionalità o il ruolo deve essere aggiunto, impostare questa proprietà su "Present". Per specificare che la funzionalità o il ruolo venga rimosso, impostare la proprietà su "Absent".| 
| IncludeAllSubFeature| Impostare questa proprietà su __$true__ per specificare lo stato di tutte le funzionalità secondarie necessarie insieme allo stato della funzionalità specificata con la proprietà __Name__.| 
| LogPath| Indica il percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.| 
| DependsOn| Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 
| Source| Indica il percorso del file di origine da usare per l'installazione, se necessario.| 

## Esempio
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```




<!--HONumber=Jun16_HO4-->


