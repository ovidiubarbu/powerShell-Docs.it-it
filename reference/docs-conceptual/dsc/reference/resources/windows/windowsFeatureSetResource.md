---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsFeatureSet DSC
ms.openlocfilehash: 1758d248dde4fdee57bd01c157a3f9a8340d6194
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71952958"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="6185e-103">Risorsa WindowsFeatureSet DSC</span><span class="sxs-lookup"><span data-stu-id="6185e-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="6185e-104">Si applica a: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="6185e-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="6185e-105">La risorsa **WindowsFeatureSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare le funzionalità e i ruoli aggiunti in un nodo di destinazione o rimossi da quest'ultimo.</span><span class="sxs-lookup"><span data-stu-id="6185e-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span> <span data-ttu-id="6185e-106">Questa risorsa è una [risorsa composita](../../../resources/authoringResourceComposite.md) che chiama la [risorsa WindowsFeature](windowsfeatureResource.md) per ogni funzionalità specificata nella proprietà **Name**.</span><span class="sxs-lookup"><span data-stu-id="6185e-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="6185e-107">Usare questa risorsa quando si vogliono configurare diverse istanze di WindowsFeature nello stesso stato.</span><span class="sxs-lookup"><span data-stu-id="6185e-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="6185e-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6185e-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="6185e-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6185e-109">Properties</span></span>

|  <span data-ttu-id="6185e-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6185e-110">Property</span></span>  |  <span data-ttu-id="6185e-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6185e-111">Description</span></span>   |
|---|---|
|<span data-ttu-id="6185e-112">Nome</span><span class="sxs-lookup"><span data-stu-id="6185e-112">Name</span></span> |<span data-ttu-id="6185e-113">Nomi dei ruoli o delle funzionalità che si vogliono aggiungere o rimuovere.</span><span class="sxs-lookup"><span data-stu-id="6185e-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="6185e-114">Corrisponde alla proprietà **Name** del cmdlet [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) e non al nome visualizzato dei ruoli o delle funzionalità.</span><span class="sxs-lookup"><span data-stu-id="6185e-114">This is the same as the **Name** property of the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) cmdlet, and not the display name of the roles or features.</span></span> |
|<span data-ttu-id="6185e-115">Source (Sorgente)</span><span class="sxs-lookup"><span data-stu-id="6185e-115">Source</span></span> |<span data-ttu-id="6185e-116">Indica il percorso del file di origine da usare per l'installazione, se necessario.</span><span class="sxs-lookup"><span data-stu-id="6185e-116">Indicates the location of the source file to use for installation, if necessary.</span></span> |
|<span data-ttu-id="6185e-117">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="6185e-117">IncludeAllSubFeature</span></span> |<span data-ttu-id="6185e-118">Impostare questa proprietà su `$true` per includere tutte le funzionalità secondarie necessarie insieme alle funzionalità specificata con la proprietà **Name**.</span><span class="sxs-lookup"><span data-stu-id="6185e-118">Set this property to `$true` to include all required subfeatures with of the features you specify with the **Name** property.</span></span> |
|<span data-ttu-id="6185e-119">Credenziale</span><span class="sxs-lookup"><span data-stu-id="6185e-119">Credential</span></span> |<span data-ttu-id="6185e-120">Credenziali da usare per aggiungere o rimuovere i ruoli o le funzionalità.</span><span class="sxs-lookup"><span data-stu-id="6185e-120">The credentials to use to add or remove the roles or features.</span></span> |
|<span data-ttu-id="6185e-121">LogPath</span><span class="sxs-lookup"><span data-stu-id="6185e-121">LogPath</span></span> |<span data-ttu-id="6185e-122">Percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.</span><span class="sxs-lookup"><span data-stu-id="6185e-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="6185e-123">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="6185e-123">Common properties</span></span>

|<span data-ttu-id="6185e-124">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6185e-124">Property</span></span> |<span data-ttu-id="6185e-125">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6185e-125">Description</span></span> |
|---|---|
|<span data-ttu-id="6185e-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6185e-126">DependsOn</span></span> |<span data-ttu-id="6185e-127">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="6185e-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6185e-128">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="6185e-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="6185e-129">Ensure</span><span class="sxs-lookup"><span data-stu-id="6185e-129">Ensure</span></span> |<span data-ttu-id="6185e-130">Indica se i ruoli o le funzionalità vengono aggiunte.</span><span class="sxs-lookup"><span data-stu-id="6185e-130">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="6185e-131">Per assicurarsi che i ruoli o le funzionalità vengano aggiunti, impostare questa proprietà su **Present**.</span><span class="sxs-lookup"><span data-stu-id="6185e-131">To ensure that the roles or features are added, set this property to **Present**.</span></span> <span data-ttu-id="6185e-132">Per assicurarsi che i ruoli o le funzionalità vengano rimossi, impostare la proprietà su **Absent**.</span><span class="sxs-lookup"><span data-stu-id="6185e-132">To ensure that the roles or features are removed, set the property to **Absent**.</span></span> <span data-ttu-id="6185e-133">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="6185e-133">The default value is **Present**.</span></span> |
|<span data-ttu-id="6185e-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="6185e-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="6185e-135">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="6185e-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="6185e-136">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="6185e-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="6185e-137">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="6185e-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="6185e-138">Esempio</span><span class="sxs-lookup"><span data-stu-id="6185e-138">Example</span></span>

<span data-ttu-id="6185e-139">La configurazione seguente garantisce che siano installate tutte le funzionalità e le funzionalità secondarie del **server Web** (IIS) e del **server SMTP**.</span><span class="sxs-lookup"><span data-stu-id="6185e-139">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

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