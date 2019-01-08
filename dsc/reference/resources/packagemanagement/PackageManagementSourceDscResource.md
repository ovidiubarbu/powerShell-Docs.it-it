---
ms.date: 06/20/2018
keywords: dsc,powershell,configurazione,installazione
title: Risorsa PackageManagementSource DSC
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047527"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="19fd9-103">Risorsa PackageManagementSource DSC</span><span class="sxs-lookup"><span data-stu-id="19fd9-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="19fd9-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="19fd9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="19fd9-105">La risorsa **PackageManagementSource** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per registrare o annullare la registrazione di origini di Gestione pacchetti in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="19fd9-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="19fd9-106">**Le origini di Gestione pacchetti registrate in questo modo vengono registrate nel contesto del sistema, utilizzabile dall'account di sistema o dal motore di DSC.**</span><span class="sxs-lookup"><span data-stu-id="19fd9-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="19fd9-107">Questa risorsa richiede il modulo **PackageManagement**, disponibile da http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="19fd9-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="19fd9-108">La versione del modulo **PackageManagement** deve essere almeno la 1.1.7.0 affinché le informazioni sulle proprietà seguenti siano corrette.</span><span class="sxs-lookup"><span data-stu-id="19fd9-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="19fd9-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="19fd9-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="19fd9-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="19fd9-110">Properties</span></span>

|  <span data-ttu-id="19fd9-111">Proprietà</span><span class="sxs-lookup"><span data-stu-id="19fd9-111">Property</span></span>  |  <span data-ttu-id="19fd9-112">Description</span><span class="sxs-lookup"><span data-stu-id="19fd9-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="19fd9-113">Nome</span><span class="sxs-lookup"><span data-stu-id="19fd9-113">Name</span></span>| <span data-ttu-id="19fd9-114">Specifica il nome dell'origine del pacchetto da registrare o di cui annullare la registrazione nel sistema.</span><span class="sxs-lookup"><span data-stu-id="19fd9-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="19fd9-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="19fd9-115">ProviderName</span></span>| <span data-ttu-id="19fd9-116">Specifica il nome del provider OneGet tramite il quale è possibile l'interoperabilità con l'origine del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="19fd9-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="19fd9-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="19fd9-117">SourceLocation</span></span>| <span data-ttu-id="19fd9-118">Specifica l'URI dell'origine del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="19fd9-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="19fd9-119">Ensure</span><span class="sxs-lookup"><span data-stu-id="19fd9-119">Ensure</span></span>| <span data-ttu-id="19fd9-120">Determina se l'origine del pacchetto deve essere registrata oppure se ne deve essere annullata la registrazione.</span><span class="sxs-lookup"><span data-stu-id="19fd9-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="19fd9-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="19fd9-121">InstallationPolicy</span></span>| <span data-ttu-id="19fd9-122">Usato dai provider, ad esempio il provider NuGet predefinito.</span><span class="sxs-lookup"><span data-stu-id="19fd9-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="19fd9-123">Determina se considerare attendibile l'origine del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="19fd9-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="19fd9-124">Uno dei valori  o . "Non attendibile", "attendibile".</span><span class="sxs-lookup"><span data-stu-id="19fd9-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="19fd9-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="19fd9-125">SourceCredential</span></span>| <span data-ttu-id="19fd9-126">Fornisce l'accesso al pacchetto in un'origine remota.</span><span class="sxs-lookup"><span data-stu-id="19fd9-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="19fd9-127">Esempio</span><span class="sxs-lookup"><span data-stu-id="19fd9-127">Example</span></span>

<span data-ttu-id="19fd9-128">Questo esempio registra l'origine del pacchetto http://nuget.org usando la risorsa DSC **PackageManagementSource**.</span><span class="sxs-lookup"><span data-stu-id="19fd9-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

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