---
title: Risorsa Package DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: bcaf82cbafe67cc309765e16b3c9cd6eff0a982a

---

# Risorsa Package DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa **Package** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per installare o disinstallare pacchetti, ad esempio i pacchetti di Windows Installer e setup.exe, nei nodi di destinazione.

## Sintassi

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## Proprietà
|  Proprietà  |  Descrizione   | 
|---|---| 
| Name| Indica il nome del pacchetto per cui si vuole specificare un determinato stato.| 
| Path| Percorso in cui si trova il pacchetto.| 
| ProductId| Indica l'ID prodotto che identifica in modo univoco il pacchetto.| 
| Arguments| Elenca una stringa di argomenti che verrà passata al pacchetto esattamente nel modo specificato.| 
| Credential| Fornisce l'accesso al pacchetto in un'origine remota. Questa proprietà non viene usata per installare il pacchetto. Il pacchetto viene sempre installato nel sistema locale.| 
| Ensure| Indica se il pacchetto è installato. Impostare questa proprietà su "Absent" per specificare che il pacchetto non è installato (o disinstallare il pacchetto se è installato). Impostarla su "Present" (valore predefinito) per specificare che il pacchetto è installato.| 
| LogPath| Indica il percorso completo in cui il provider deve salvare un file di log per installare o disinstallare il pacchetto.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"``.| 
| ReturnCode| Indica il codice restituito previsto. Se l'effettivo codice restituito non corrisponde al valore previsto specificato qui, la configurazione restituirà un errore.| 

## Esempio

Questo esempio esegue il programma di installazione MSI che si trova nel percorso specificato e che ha l'ID prodotto indicato.

```powershell
Package PackageExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path  = "$Env:SystemDrive\TestFolder\TestProject.msi"
    Name = "TestPackage"
    ProductId = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
} 
```




<!--HONumber=Jun16_HO4-->


