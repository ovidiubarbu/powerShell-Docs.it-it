---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa PackageManagementSource DSC
ms.openlocfilehash: 20b7851e44751d4bd0add718d2f7294d5215ab70
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954788"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="81470-103">Risorsa PackageManagementSource DSC</span><span class="sxs-lookup"><span data-stu-id="81470-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="81470-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="81470-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="81470-105">La risorsa **PackageManagementSource** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per registrare o annullare la registrazione di origini di Gestione pacchetti in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="81470-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span>
<span data-ttu-id="81470-106">**Le origini di Gestione pacchetti registrate in questo modo vengono registrate nel contesto del sistema, utilizzabile dall'account di sistema o dal motore di DSC.**</span><span class="sxs-lookup"><span data-stu-id="81470-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="81470-107">Questa risorsa richiede il modulo **PackageManagement**, disponibile da [PowerShell Gallery](https://PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="81470-107">This resource requires the **PackageManagement** module, available from the [PowerShell Gallery](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="81470-108">La versione del modulo **PackageManagement** deve essere almeno la 1.1.7.0 affinché le informazioni sulle proprietà seguenti siano corrette.</span><span class="sxs-lookup"><span data-stu-id="81470-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="81470-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="81470-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="81470-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="81470-110">Properties</span></span>

|<span data-ttu-id="81470-111">Proprietà</span><span class="sxs-lookup"><span data-stu-id="81470-111">Property</span></span> |<span data-ttu-id="81470-112">Description</span><span class="sxs-lookup"><span data-stu-id="81470-112">Description</span></span> |
|---|---|
|<span data-ttu-id="81470-113">Nome</span><span class="sxs-lookup"><span data-stu-id="81470-113">Name</span></span> |<span data-ttu-id="81470-114">Specifica il nome dell'origine del pacchetto da registrare o di cui annullare la registrazione nel sistema.</span><span class="sxs-lookup"><span data-stu-id="81470-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span> |
|<span data-ttu-id="81470-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="81470-115">ProviderName</span></span> |<span data-ttu-id="81470-116">Specifica il nome del provider OneGet tramite il quale è possibile l'interoperabilità con l'origine del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="81470-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span> |
|<span data-ttu-id="81470-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="81470-117">SourceLocation</span></span> |<span data-ttu-id="81470-118">Specifica l'URI dell'origine del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="81470-118">Specifies the URI of the package source.</span></span> |
|<span data-ttu-id="81470-119">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="81470-119">InstallationPolicy</span></span> |<span data-ttu-id="81470-120">Usato dai provider, ad esempio il provider NuGet predefinito.</span><span class="sxs-lookup"><span data-stu-id="81470-120">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="81470-121">Determina se considerare attendibile l'origine del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="81470-121">Determines whether you trust the package's source.</span></span> <span data-ttu-id="81470-122">Uno dei valori possibili: **Untrusted** o **Trusted**.</span><span class="sxs-lookup"><span data-stu-id="81470-122">One of: **Untrusted** or **Trusted**.</span></span> |
|<span data-ttu-id="81470-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="81470-123">SourceCredential</span></span> |<span data-ttu-id="81470-124">Fornisce l'accesso al pacchetto in un'origine remota.</span><span class="sxs-lookup"><span data-stu-id="81470-124">Provides access to the package on a remote source.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="81470-125">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="81470-125">Common properties</span></span>

|<span data-ttu-id="81470-126">Proprietà</span><span class="sxs-lookup"><span data-stu-id="81470-126">Property</span></span> |<span data-ttu-id="81470-127">Description</span><span class="sxs-lookup"><span data-stu-id="81470-127">Description</span></span> |
|---|---|
|<span data-ttu-id="81470-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="81470-128">DependsOn</span></span> |<span data-ttu-id="81470-129">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="81470-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="81470-130">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="81470-130">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="81470-131">Ensure</span><span class="sxs-lookup"><span data-stu-id="81470-131">Ensure</span></span> |<span data-ttu-id="81470-132">Determina se l'origine del pacchetto deve essere registrata oppure se ne deve essere annullata la registrazione.</span><span class="sxs-lookup"><span data-stu-id="81470-132">Determines whether the package source is to be registered or unregistered.</span></span> <span data-ttu-id="81470-133">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="81470-133">The default value is **Present**.</span></span> |
|<span data-ttu-id="81470-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="81470-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="81470-135">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="81470-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="81470-136">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="81470-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="81470-137">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="81470-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="81470-138">Esempio</span><span class="sxs-lookup"><span data-stu-id="81470-138">Example</span></span>

<span data-ttu-id="81470-139">Questo esempio registra l'origine del pacchetto `https://nuget.org` usando la risorsa DSC **PackageManagementSource**.</span><span class="sxs-lookup"><span data-stu-id="81470-139">This example registers the `https://nuget.org` package source using the **PackageManagementSource** DSC resource.</span></span>

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