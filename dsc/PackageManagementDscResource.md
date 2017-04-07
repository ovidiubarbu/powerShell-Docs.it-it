---
title: Risorsa PackageManagement DSC
ms.date: 
keywords: powershell,DSC
description: 
ms.topic: article
author: brywang-msft
manager: kriscv
ms.prod: powershell
ms.openlocfilehash: 33775be230a4e92e22784d991338510510f69889
ms.sourcegitcommit: 89e7ae30faff5f96641fc72764bdc76e0e257bc2
translationtype: HT
---
# <a name="dsc-packagemanagement-resource"></a>Risorsa PackageManagement DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa **PackageManagement** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per installare o disinstallare pacchetti di Gestione pacchetti in un nodo di destinazione. Questa risorsa richiede il modulo **PackageManagement**, disponibile da http://PowerShellGallery.com.

## <a name="syntax"></a>Sintassi

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a>Proprietà
|  Proprietà  |  Descrizione   | 
|---|---| 
| Nome| Specifica il nome del pacchetto da installare o disinstallare.| 
| Source| Specifica il nome dell'origine del pacchetto in cui è possibile trovare il pacchetto. Può trattarsi di un URI o di un'origine registrata con la risorsa DSC Register-PackageSource o PackageManagementSource. La risorsa DSC MSFT_PackageManagementSource può anche registrare un'origine del pacchetto.| 
| Ensure| Determina se il pacchetto deve essere installato o disinstallato.| 
| RequiredVersion| Specifica la versione esatta del pacchetto da installare. Se non si specifica questo parametro, la risorsa DSC installa la versione disponibile più recente del pacchetto che soddisfa anche l'eventuale requisito di versione massima specificato dal parametro MaximumVersion.| 
| MinimumVersion| Specifica la versione minima consentita del pacchetto da installare. Se non si aggiunge questo parametro, la risorsa DSC installa la versione disponibile più recente del pacchetto che soddisfa anche l'eventuale requisito di versione massima specificato dal parametro MaximumVersion.| 
| MaximumVersion| Specifica la versione massima consentita del pacchetto da installare. Se non si specifica questo parametro, questa risorsa DSC installa la versione disponibile con numero più alto del pacchetto.| 
| SourceCredential | Specifica un account utente con i diritti per installare un pacchetto per un'origine o un provider di pacchetti specificato.| 
| ProviderName| Specifica il nome di un provider di pacchetti entro il cui ambito limitare la ricerca di pacchetti. Per ottenere i nomi di provider di pacchetti, è possibile eseguire il cmdlet Get-PackageProvider.| 
| AdditionalParameters| Parametri specifici del provider che vengono passati come una tabella hash. Ad esempio, per il provider NuGet è possibile passare parametri aggiuntivi come DestinationPath.| 

## <a name="additional-parameters"></a>Parametri aggiuntivi
Nella tabella seguente sono elencate le opzioni per la proprietà AdditionalParameters.
|  Parametro  | Description   | 
|---|---|
| DestinationPath| Usato dai provider, ad esempio il provider NuGet predefinito. Specifica un percorso di file in cui si vuole installare il pacchetto.|
| InstallationPolicy| Usato dai provider, ad esempio il provider NuGet predefinito. Determina se considerare attendibile l'origine del pacchetto. Uno dei valori possibili: "Untrusted", "Trusted".|

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
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }    
    
    PackageManagementSource PSGallery 
    { 
        Ensure      = "Present" 
        Name        = "psgallery" 
        ProviderName= "PowerShellGet" 
        SourceUri   = "https://www.powershellgallery.com/api/v2/"   
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