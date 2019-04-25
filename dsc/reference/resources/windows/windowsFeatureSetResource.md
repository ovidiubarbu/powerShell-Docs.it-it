---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsFeatureSet DSC
ms.openlocfilehash: 8b7c7e72dd58459bd19cb723e5790a82841515c0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076787"
---
# <a name="dsc-windowsfeatureset-resource"></a>Risorsa WindowsFeatureSet DSC

> Si applica a: Windows PowerShell 5.0

La risorsa **WindowsFeatureSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare le funzionalità e i ruoli aggiunti in un nodo di destinazione o rimossi da quest'ultimo.
Questa risorsa è una [risorsa composta](../../../resources/authoringResourceComposite.md) che chiama la [risorsa WindowsFeature](windowsfeatureResource.md) per ogni funzionalità specificata nella proprietà `Name`.

Usare questa risorsa quando si vogliono configurare diverse istanze di WindowsFeature nello stesso stato.

## <a name="syntax"></a>Sintassi

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Proprietà

|  Proprietà  |  Description   |
|---|---|
| Nome| Nomi dei ruoli o delle funzionalità che si vogliono aggiungere o rimuovere. Corrisponde alla proprietà **Name** del cmdlet [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) e non al nome visualizzato dei ruoli o delle funzionalità.|
| Credential| Credenziali da usare per aggiungere o rimuovere i ruoli o le funzionalità.|
| Ensure| Indica se i ruoli o le funzionalità vengono aggiunte. Per specificare che i ruoli o le funzionalità devono essere aggiunte, impostare questa proprietà su "Present". Per specificare che i ruoli o le funzionalità devono essere rimosse, impostare la proprietà su "Absent".|
| IncludeAllSubFeature| Impostare questa proprietà su **$true** per specificare tutte le funzionalità secondarie necessarie insieme alla funzionalità specificata con la proprietà **Name**.|
| LogPath| Percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.|
| DependsOn| Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|
| Source| Indica il percorso del file di origine da usare per l'installazione, se necessario.|

## <a name="example"></a>Esempio

La configurazione seguente garantisce che siano installate tutte le funzionalità e le funzionalità secondarie del **server Web** (IIS) e del **server SMTP**.

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```
