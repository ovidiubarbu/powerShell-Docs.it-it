---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsPackageCab DSC
ms.openlocfilehash: 8c4de193c8ea787dd125436f86aa0b5eafdb1509
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-windowspackagecab-resource"></a>Risorsa WindowsPackageCab DSC

> Si applica a: Windows PowerShell 5.1 e versioni successive

La risorsa **WindowsPackageCab** in Windows PowerShell DSC (Desired State Configuration) offre un meccanismo per installare o disinstallare pacchetti CAB in un nodo di destinazione.

È necessario che nel nodo di destinazione sia installato il modulo PowerShell Gestione e manutenzione immagini distribuzione. Per informazioni, vedere [Usare Gestione e manutenzione immagini distribuzione in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).


## <a name="syntax"></a>Sintassi

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Proprietà

|  Proprietà  |  Description   |
|---|---|
| Nome| Indica il nome del pacchetto per cui si vuole specificare un determinato stato.|
| Ensure| Indica se il pacchetto è installato. Impostare questa proprietà su "Absent" per specificare che il pacchetto non è installato (o disinstallare il pacchetto se è installato). Impostarla su "Present" (valore predefinito) per specificare che il pacchetto è installato.|
| Path| Percorso in cui si trova il pacchetto.|
| LogPath| Indica il percorso completo in cui il provider deve salvare un file di log per installare o disinstallare il pacchetto.|
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"``.|

## <a name="example"></a>Esempio

La configurazione di esempio seguente accetta parametri di input e assicura che venga installato il file con estensione cab specificato dal parametro `$Name`.

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```