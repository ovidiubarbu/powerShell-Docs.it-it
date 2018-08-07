---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Package DSC
ms.openlocfilehash: 9285df71a303c9a53dd50d450272575a64e962e7
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268671"
---
# <a name="dsc-package-resource"></a>Risorsa Package DSC

_Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0_

La risorsa **Package** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per installare o disinstallare pacchetti, ad esempio i pacchetti di Windows Installer e setup.exe, nei nodi di destinazione.

## <a name="syntax"></a>Sintassi

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

## <a name="properties"></a>Proprietà

| Proprietà | Description |
| --- | --- |
| Nome| Indica il nome del pacchetto per cui si vuole specificare un determinato stato.|
| Path| Percorso in cui si trova il pacchetto.|
| ProductId| Indica l'ID prodotto che identifica in modo univoco il pacchetto.|
| Arguments| Elenca una stringa di argomenti che verrà passata al pacchetto esattamente nel modo specificato.|
| Credential| Fornisce l'accesso al pacchetto in un'origine remota. Questa proprietà non viene usata per installare il pacchetto. Il pacchetto viene sempre installato nel sistema locale.|
| Ensure| Indica se il pacchetto è installato. Impostare questa proprietà su "Absent" per specificare che il pacchetto non è installato (o disinstallare il pacchetto se è installato). Impostarla su "Present" (valore predefinito) per specificare che il pacchetto è installato.|
| LogPath| Indica il percorso completo in cui il provider deve salvare un file di log per installare o disinstallare il pacchetto.|
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|
| ReturnCode| Indica il codice restituito previsto. Se l'effettivo codice restituito non corrisponde al valore previsto specificato qui, la configurazione restituirà un errore.|

## <a name="example"></a>Esempio

Questo esempio esegue il programma di installazione MSI che si trova nel percorso specificato e che ha l'ID prodotto indicato.

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```