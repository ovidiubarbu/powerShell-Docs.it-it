---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsFeature DSC
ms.openlocfilehash: d3384b1f45324df6b6b209f25b64d9d77615ad7f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954628"
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="d670a-103">Risorsa WindowsFeature DSC</span><span class="sxs-lookup"><span data-stu-id="d670a-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="d670a-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="d670a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="d670a-105">La risorsa **WindowsFeature** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare che funzionalità e ruoli vengano aggiunti o rimossi in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="d670a-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="d670a-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d670a-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="d670a-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="d670a-107">Properties</span></span>

|<span data-ttu-id="d670a-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="d670a-108">Property</span></span> |<span data-ttu-id="d670a-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="d670a-109">Description</span></span> |
|---|---|
|<span data-ttu-id="d670a-110">Nome</span><span class="sxs-lookup"><span data-stu-id="d670a-110">Name</span></span> |<span data-ttu-id="d670a-111">Indica il nome del ruolo o della funzionalità che si vuole aggiungere o rimuovere.</span><span class="sxs-lookup"><span data-stu-id="d670a-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="d670a-112">Corrisponde alla proprietà **Name** del cmdlet [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) e non al nome visualizzato del ruolo o della funzionalità.</span><span class="sxs-lookup"><span data-stu-id="d670a-112">This is the same as the **Name** property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span> |
|<span data-ttu-id="d670a-113">Credenziale</span><span class="sxs-lookup"><span data-stu-id="d670a-113">Credential</span></span> |<span data-ttu-id="d670a-114">Indica le credenziali da usare per aggiungere o rimuovere il ruolo o la funzionalità.</span><span class="sxs-lookup"><span data-stu-id="d670a-114">Indicates the credentials to use to add or remove the role or feature.</span></span> |
|<span data-ttu-id="d670a-115">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="d670a-115">IncludeAllSubFeature</span></span> |<span data-ttu-id="d670a-116">Impostare questa proprietà su `$true` per specificare lo stato di tutte le funzionalità secondarie necessarie insieme allo stato della funzionalità specificata con la proprietà **Name**.</span><span class="sxs-lookup"><span data-stu-id="d670a-116">Set this property to `$true` to ensure the state of all required subfeatures with the state of the feature you specify with the **Name** property.</span></span> |
|<span data-ttu-id="d670a-117">LogPath</span><span class="sxs-lookup"><span data-stu-id="d670a-117">LogPath</span></span> |<span data-ttu-id="d670a-118">Indica il percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.</span><span class="sxs-lookup"><span data-stu-id="d670a-118">Indicates the path to a log file where you want the resource provider to log the operation.</span></span> |
|<span data-ttu-id="d670a-119">Source (Sorgente)</span><span class="sxs-lookup"><span data-stu-id="d670a-119">Source</span></span> |<span data-ttu-id="d670a-120">Indica il percorso del file di origine da usare per l'installazione, se necessario.</span><span class="sxs-lookup"><span data-stu-id="d670a-120">Indicates the location of the source file to use for installation, if necessary.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="d670a-121">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="d670a-121">Common properties</span></span>

|<span data-ttu-id="d670a-122">Proprietà</span><span class="sxs-lookup"><span data-stu-id="d670a-122">Property</span></span> |<span data-ttu-id="d670a-123">Descrizione</span><span class="sxs-lookup"><span data-stu-id="d670a-123">Description</span></span> |
|---|---|
|<span data-ttu-id="d670a-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d670a-124">DependsOn</span></span> |<span data-ttu-id="d670a-125">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="d670a-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d670a-126">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d670a-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="d670a-127">Ensure</span><span class="sxs-lookup"><span data-stu-id="d670a-127">Ensure</span></span> |<span data-ttu-id="d670a-128">Indica se la funzionalità o il ruolo viene aggiunto.</span><span class="sxs-lookup"><span data-stu-id="d670a-128">Indicates if the role or feature is added.</span></span> <span data-ttu-id="d670a-129">Per assicurarsi che il ruolo o la funzionalità venga aggiunta, impostare questa proprietà su **Present**.</span><span class="sxs-lookup"><span data-stu-id="d670a-129">To ensure that the role or feature is added, set this property to **Present**.</span></span> <span data-ttu-id="d670a-130">Per assicurarsi che il ruolo o la funzionalità venga rimossa, impostare la proprietà su **Absent**.</span><span class="sxs-lookup"><span data-stu-id="d670a-130">To ensure that the role or feature is removed, set the property to **Absent**.</span></span> <span data-ttu-id="d670a-131">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="d670a-131">The default value is **Present**.</span></span> |
|<span data-ttu-id="d670a-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d670a-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="d670a-133">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="d670a-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="d670a-134">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="d670a-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="d670a-135">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="d670a-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="d670a-136">Esempio</span><span class="sxs-lookup"><span data-stu-id="d670a-136">Example</span></span>

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```