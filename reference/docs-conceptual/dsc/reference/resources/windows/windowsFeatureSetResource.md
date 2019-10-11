---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsFeatureSet DSC
ms.openlocfilehash: 1758d248dde4fdee57bd01c157a3f9a8340d6194
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952958"
---
# <a name="dsc-windowsfeatureset-resource"></a>Risorsa WindowsFeatureSet DSC

> Si applica a: Windows PowerShell 5.x

La risorsa **WindowsFeatureSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare le funzionalità e i ruoli aggiunti in un nodo di destinazione o rimossi da quest'ultimo. Questa risorsa è una [risorsa composita](../../../resources/authoringResourceComposite.md) che chiama la [risorsa WindowsFeature](windowsfeatureResource.md) per ogni funzionalità specificata nella proprietà **Name**.

Usare questa risorsa quando si vogliono configurare diverse istanze di WindowsFeature nello stesso stato.

## <a name="syntax"></a>Sintassi

```Syntax
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [Boolean] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|  Proprietà  |  Description   |
|---|---|
|Nome |Nomi dei ruoli o delle funzionalità che si vogliono aggiungere o rimuovere. Corrisponde alla proprietà **Name** del cmdlet [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) e non al nome visualizzato dei ruoli o delle funzionalità. |
|Source |Indica il percorso del file di origine da usare per l'installazione, se necessario. |
|IncludeAllSubFeature |Impostare questa proprietà su `$true` per includere tutte le funzionalità secondarie necessarie insieme alle funzionalità specificata con la proprietà **Name**. |
|Credential |Credenziali da usare per aggiungere o rimuovere i ruoli o le funzionalità. |
|LogPath |Percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica se i ruoli o le funzionalità vengono aggiunte. Per assicurarsi che i ruoli o le funzionalità vengano aggiunti, impostare questa proprietà su **Present**. Per assicurarsi che i ruoli o le funzionalità vengano rimossi, impostare la proprietà su **Absent**. Il valore predefinito è **Present**. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).

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