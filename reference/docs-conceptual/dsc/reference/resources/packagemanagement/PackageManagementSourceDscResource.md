---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa PackageManagementSource DSC
ms.openlocfilehash: 20b7851e44751d4bd0add718d2f7294d5215ab70
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954788"
---
# <a name="dsc-packagemanagementsource-resource"></a>Risorsa PackageManagementSource DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x

La risorsa **PackageManagementSource** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per registrare o annullare la registrazione di origini di Gestione pacchetti in un nodo di destinazione.
**Le origini di Gestione pacchetti registrate in questo modo vengono registrate nel contesto del sistema, utilizzabile dall'account di sistema o dal motore di DSC.** Questa risorsa richiede il modulo **PackageManagement**, disponibile da [PowerShell Gallery](https://PowerShellGallery.com).

> [!IMPORTANT]
> La versione del modulo **PackageManagement** deve essere almeno la 1.1.7.0 affinché le informazioni sulle proprietà seguenti siano corrette.

## <a name="syntax"></a>Sintassi

```Syntax
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [ InstallationPolicy = [string]{ Trusted | Untrusted } ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Descrizione |
|---|---|
|Nome |Specifica il nome dell'origine del pacchetto da registrare o di cui annullare la registrazione nel sistema. |
|ProviderName |Specifica il nome del provider OneGet tramite il quale è possibile l'interoperabilità con l'origine del pacchetto. |
|SourceLocation |Specifica l'URI dell'origine del pacchetto. |
|InstallationPolicy |Usato dai provider, ad esempio il provider NuGet predefinito. Determina se considerare attendibile l'origine del pacchetto. Uno dei valori possibili: **Untrusted** o **Trusted**. |
|SourceCredential |Fornisce l'accesso al pacchetto in un'origine remota. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Descrizione |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Determina se l'origine del pacchetto deve essere registrata oppure se ne deve essere annullata la registrazione. Il valore predefinito è **Present**. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Esempio

Questo esempio registra l'origine del pacchetto `https://nuget.org` usando la risorsa DSC **PackageManagementSource**.

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "https://api.nuget.org/api/v3/"
        InstallationPolicy ="Trusted"
    }
}
```