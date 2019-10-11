---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsFeature DSC
ms.openlocfilehash: d3384b1f45324df6b6b209f25b64d9d77615ad7f
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954628"
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="1b90e-103">Risorsa WindowsFeature DSC</span><span class="sxs-lookup"><span data-stu-id="1b90e-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="1b90e-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="1b90e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="1b90e-105">La risorsa **WindowsFeature** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare che funzionalità e ruoli vengano aggiunti o rimossi in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="1b90e-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b90e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1b90e-106">Syntax</span></span>

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ Source = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="1b90e-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="1b90e-107">Properties</span></span>

|<span data-ttu-id="1b90e-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="1b90e-108">Property</span></span> |<span data-ttu-id="1b90e-109">Description</span><span class="sxs-lookup"><span data-stu-id="1b90e-109">Description</span></span> |
|---|---|
|<span data-ttu-id="1b90e-110">Nome</span><span class="sxs-lookup"><span data-stu-id="1b90e-110">Name</span></span> |<span data-ttu-id="1b90e-111">Indica il nome del ruolo o della funzionalità che si vuole aggiungere o rimuovere.</span><span class="sxs-lookup"><span data-stu-id="1b90e-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="1b90e-112">Corrisponde alla proprietà **Name** del cmdlet [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) e non al nome visualizzato del ruolo o della funzionalità.</span><span class="sxs-lookup"><span data-stu-id="1b90e-112">This is the same as the **Name** property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span> |
|<span data-ttu-id="1b90e-113">Credential</span><span class="sxs-lookup"><span data-stu-id="1b90e-113">Credential</span></span> |<span data-ttu-id="1b90e-114">Indica le credenziali da usare per aggiungere o rimuovere il ruolo o la funzionalità.</span><span class="sxs-lookup"><span data-stu-id="1b90e-114">Indicates the credentials to use to add or remove the role or feature.</span></span> |
|<span data-ttu-id="1b90e-115">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="1b90e-115">IncludeAllSubFeature</span></span> |<span data-ttu-id="1b90e-116">Impostare questa proprietà su `$true` per specificare lo stato di tutte le funzionalità secondarie necessarie insieme allo stato della funzionalità specificata con la proprietà **Name**.</span><span class="sxs-lookup"><span data-stu-id="1b90e-116">Set this property to `$true` to ensure the state of all required subfeatures with the state of the feature you specify with the **Name** property.</span></span> |
|<span data-ttu-id="1b90e-117">LogPath</span><span class="sxs-lookup"><span data-stu-id="1b90e-117">LogPath</span></span> |<span data-ttu-id="1b90e-118">Indica il percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.</span><span class="sxs-lookup"><span data-stu-id="1b90e-118">Indicates the path to a log file where you want the resource provider to log the operation.</span></span> |
|<span data-ttu-id="1b90e-119">Source</span><span class="sxs-lookup"><span data-stu-id="1b90e-119">Source</span></span> |<span data-ttu-id="1b90e-120">Indica il percorso del file di origine da usare per l'installazione, se necessario.</span><span class="sxs-lookup"><span data-stu-id="1b90e-120">Indicates the location of the source file to use for installation, if necessary.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="1b90e-121">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="1b90e-121">Common properties</span></span>

|<span data-ttu-id="1b90e-122">Proprietà</span><span class="sxs-lookup"><span data-stu-id="1b90e-122">Property</span></span> |<span data-ttu-id="1b90e-123">Description</span><span class="sxs-lookup"><span data-stu-id="1b90e-123">Description</span></span> |
|---|---|
|<span data-ttu-id="1b90e-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1b90e-124">DependsOn</span></span> |<span data-ttu-id="1b90e-125">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="1b90e-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1b90e-126">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="1b90e-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="1b90e-127">Ensure</span><span class="sxs-lookup"><span data-stu-id="1b90e-127">Ensure</span></span> |<span data-ttu-id="1b90e-128">Indica se la funzionalità o il ruolo viene aggiunto.</span><span class="sxs-lookup"><span data-stu-id="1b90e-128">Indicates if the role or feature is added.</span></span> <span data-ttu-id="1b90e-129">Per assicurarsi che il ruolo o la funzionalità venga aggiunta, impostare questa proprietà su **Present**.</span><span class="sxs-lookup"><span data-stu-id="1b90e-129">To ensure that the role or feature is added, set this property to **Present**.</span></span> <span data-ttu-id="1b90e-130">Per assicurarsi che il ruolo o la funzionalità venga rimossa, impostare la proprietà su **Absent**.</span><span class="sxs-lookup"><span data-stu-id="1b90e-130">To ensure that the role or feature is removed, set the property to **Absent**.</span></span> <span data-ttu-id="1b90e-131">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="1b90e-131">The default value is **Present**.</span></span> |
|<span data-ttu-id="1b90e-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="1b90e-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="1b90e-133">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="1b90e-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="1b90e-134">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="1b90e-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="1b90e-135">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="1b90e-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="1b90e-136">Esempio</span><span class="sxs-lookup"><span data-stu-id="1b90e-136">Example</span></span>

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```