---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa PackageManagementSource DSC
ms.openlocfilehash: 8c0cb5a3b0a019ddb5ed995406f499298103b07c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="af223-103">Risorsa PackageManagementSource DSC</span><span class="sxs-lookup"><span data-stu-id="af223-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="af223-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="af223-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="af223-105">La risorsa **PackageManagementSource** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per registrare o annullare la registrazione di origini di Gestione pacchetti in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="af223-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="af223-106">**Le origini di Gestione pacchetti registrate in questo modo vengono registrate nel contesto del sistema, utilizzabile dall'account di sistema o dal motore di DSC.**</span><span class="sxs-lookup"><span data-stu-id="af223-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="af223-107">Questa risorsa richiede il modulo **PackageManagement**, disponibile da http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="af223-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="af223-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="af223-108">Syntax</span></span>

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="af223-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="af223-109">Properties</span></span>
|  <span data-ttu-id="af223-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="af223-110">Property</span></span>  |  <span data-ttu-id="af223-111">Description</span><span class="sxs-lookup"><span data-stu-id="af223-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="af223-112">Nome</span><span class="sxs-lookup"><span data-stu-id="af223-112">Name</span></span>| <span data-ttu-id="af223-113">Specifica il nome dell'origine del pacchetto da registrare o di cui annullare la registrazione nel sistema.</span><span class="sxs-lookup"><span data-stu-id="af223-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="af223-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="af223-114">Ensure</span></span>| <span data-ttu-id="af223-115">Determina se l'origine del pacchetto deve essere registrata oppure se ne deve essere annullata la registrazione.</span><span class="sxs-lookup"><span data-stu-id="af223-115">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="af223-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="af223-116">InstallationPolicy</span></span>| <span data-ttu-id="af223-117">Determina se considerare attendibile l'origine del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="af223-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="af223-118">Uno dei valori possibili: "Untrusted", "Trusted".</span><span class="sxs-lookup"><span data-stu-id="af223-118">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="af223-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="af223-119">ProviderName</span></span>| <span data-ttu-id="af223-120">Specifica il nome del provider OneGet tramite il quale è possibile l'interoperabilità con l'origine del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="af223-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="af223-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="af223-121">SourceUri</span></span>| <span data-ttu-id="af223-122">Specifica l'URI dell'origine del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="af223-122">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="af223-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="af223-123">SourceCredential</span></span>| <span data-ttu-id="af223-124">Fornisce l'accesso al pacchetto in un'origine remota.</span><span class="sxs-lookup"><span data-stu-id="af223-124">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="af223-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="af223-125">Example</span></span>

<span data-ttu-id="af223-126">Questo esempio registra l'origine del pacchetto http://nuget.org usando la risorsa DSC **PackageManagementSource**.</span><span class="sxs-lookup"><span data-stu-id="af223-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```