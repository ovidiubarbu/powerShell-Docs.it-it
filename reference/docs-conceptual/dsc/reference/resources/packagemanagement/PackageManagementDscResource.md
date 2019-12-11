---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa PackageManagement DSC
ms.openlocfilehash: dfc23bfabbc45041e15c56a29a77c5bdda430a30
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953238"
---
# <a name="dsc-packagemanagement-resource"></a>Risorsa PackageManagement DSC

Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1

La risorsa **PackageManagement** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per installare o disinstallare pacchetti di Gestione pacchetti in un nodo di destinazione. Questa risorsa richiede il modulo **PackageManagement**, disponibile da [http://PowerShellGallery.com](https://PowerShellGallery.com).

> [!IMPORTANT]
> La versione del modulo **PackageManagement** deve essere almeno la 1.1.7.0 affinché le informazioni sulle proprietà seguenti siano corrette.

## <a name="syntax"></a>Sintassi

```Syntax
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ AdditionalParameters = [HashTable] ]
    [ MaximumVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ ProviderName = [string] ]
    [ RequiredVersion = [string] ]
    [ Source = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Description |
|---|---|
|Nome |Specifica il nome del pacchetto da installare o disinstallare. |
|AdditionalParameters |Tabella hash specifica del provider dei parametri passati a `Get-Package -AdditionalArguments`. Ad esempio, per il provider NuGet è possibile passare parametri aggiuntivi come DestinationPath. |
|MaximumVersion |Specifica la versione massima consentita del pacchetto da trovare. Se non si aggiunge questo parametro, la risorsa trova la versione disponibile più recente del pacchetto. |
|MinimumVersion |Specifica la versione minima consentita del pacchetto da trovare. Se non si aggiunge questo parametro, la risorsa trova la versione disponibile più recente del pacchetto che soddisfa anche l'eventuale requisito di versione massima specificato dal parametro **MaximumVersion**. |
|ProviderName |Specifica il nome di un provider di pacchetti entro il cui ambito limitare la ricerca di pacchetti. Per ottenere i nomi di provider di pacchetti, è possibile eseguire il cmdlet `Get-PackageProvider`. |
|RequiredVersion |Specifica la versione esatta del pacchetto da installare. Se non si specifica questo parametro, la risorsa DSC installa la versione disponibile più recente del pacchetto che soddisfa anche l'eventuale requisito di versione massima specificato dal parametro **MaximumVersion**. |
|Source |Specifica il nome dell'origine del pacchetto in cui è possibile trovare il pacchetto. Può trattarsi di un URI o di un'origine registrata con la risorsa DSC `Register-PackageSource` o PackageManagementSource. |
|SourceCredential |Specifica un account utente con i diritti per installare un pacchetto per un'origine o un provider di pacchetti specificato. |

## <a name="additional-parameters"></a>Parametri aggiuntivi

Nella tabella seguente sono elencate le opzioni per la proprietà AdditionalParameters.

|Parametro |Description |
|---|---|
|DestinationPath |Usato dai provider, ad esempio il provider NuGet predefinito. Specifica un percorso di file in cui si vuole installare il pacchetto. |
|InstallationPolicy |Usato dai provider, ad esempio il provider NuGet predefinito. Determina se considerare attendibile l'origine del pacchetto. Uno dei valori possibili: **Untrusted** o **Trusted**. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Determina se il pacchetto deve essere installato o disinstallato. Il valore predefinito è **Present**. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Esempio

Questo esempio installa il pacchetto NuGet **JQuery** e il modulo di PowerShell **GistProvider** usando la risorsa DSC **PackageManagement**. Questo esempio verifica innanzitutto che siano disponibili le origini di pacchetti richieste e quindi definisce lo stato previsto dei pacchetti **JQuery** e **GistProvider** (rispettivamente, NuGet e PowerShell).

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```