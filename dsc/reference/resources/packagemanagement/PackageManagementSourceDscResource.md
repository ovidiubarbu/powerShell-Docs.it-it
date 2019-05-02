---
ms.date: 06/20/2018
keywords: dsc,powershell,configurazione,installazione
title: Risorsa PackageManagementSource DSC
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077586"
---
# <a name="dsc-packagemanagementsource-resource"></a>Risorsa PackageManagementSource DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1

La risorsa **PackageManagementSource** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per registrare o annullare la registrazione di origini di Gestione pacchetti in un nodo di destinazione. **Le origini di Gestione pacchetti registrate in questo modo vengono registrate nel contesto del sistema, utilizzabile dall'account di sistema o dal motore di DSC.** Questa risorsa richiede il modulo **PackageManagement**, disponibile da http://PowerShellGallery.com.

> [!IMPORTANT]
> La versione del modulo **PackageManagement** deve essere almeno la 1.1.7.0 affinché le informazioni sulle proprietà seguenti siano corrette.

## <a name="syntax"></a>Sintassi

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Proprietà

|  Proprietà  |  Description   |
|---|---|
| Nome| Specifica il nome dell'origine del pacchetto da registrare o di cui annullare la registrazione nel sistema.|
| ProviderName| Specifica il nome del provider OneGet tramite il quale è possibile l'interoperabilità con l'origine del pacchetto.|
| SourceLocation| Specifica l'URI dell'origine del pacchetto.|
| Ensure| Determina se l'origine del pacchetto deve essere registrata oppure se ne deve essere annullata la registrazione.|
| InstallationPolicy| Usato dai provider, ad esempio il provider NuGet predefinito. Determina se considerare attendibile l'origine del pacchetto. Uno dei valori possibili: "Untrusted", "Trusted".|
| SourceCredential| Fornisce l'accesso al pacchetto in un'origine remota.|

## <a name="example"></a>Esempio

Questo esempio registra l'origine del pacchetto http://nuget.org usando la risorsa DSC **PackageManagementSource**.

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```