---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Risorsa WindowsFeature DSC
ms.openlocfilehash: b4f50cb9ee172600b1811175e9cf67f6a7ed2d55
ms.sourcegitcommit: cd5a1f054cbf9eb95c5242a995f9741e031ddb24
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2017
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="c797e-103">Risorsa WindowsFeature DSC</span><span class="sxs-lookup"><span data-stu-id="c797e-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="c797e-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c797e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c797e-105">La risorsa **WindowsFeature** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare che funzionalità e ruoli vengano aggiunti o rimossi in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="c797e-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c797e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c797e-106">Syntax</span></span>

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="c797e-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="c797e-107">Properties</span></span>

|  <span data-ttu-id="c797e-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="c797e-108">Property</span></span>  |  <span data-ttu-id="c797e-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c797e-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="c797e-110">Name</span><span class="sxs-lookup"><span data-stu-id="c797e-110">Name</span></span>| <span data-ttu-id="c797e-111">Indica il nome del ruolo o della funzionalità che si vuole aggiungere o rimuovere.</span><span class="sxs-lookup"><span data-stu-id="c797e-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="c797e-112">Corrisponde alla proprietà __Name__ del cmdlet [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) e non al nome visualizzato del ruolo o della funzionalità.</span><span class="sxs-lookup"><span data-stu-id="c797e-112">This is the same as the __Name__ property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span>| 
| <span data-ttu-id="c797e-113">Credential</span><span class="sxs-lookup"><span data-stu-id="c797e-113">Credential</span></span>| <span data-ttu-id="c797e-114">Indica le credenziali da usare per aggiungere o rimuovere il ruolo o la funzionalità.</span><span class="sxs-lookup"><span data-stu-id="c797e-114">Indicates the credentials to use to add or remove the role or feature.</span></span>| 
| <span data-ttu-id="c797e-115">Ensure</span><span class="sxs-lookup"><span data-stu-id="c797e-115">Ensure</span></span>| <span data-ttu-id="c797e-116">Indica se la funzionalità o il ruolo viene aggiunto.</span><span class="sxs-lookup"><span data-stu-id="c797e-116">Indicates if the role or feature is added.</span></span> <span data-ttu-id="c797e-117">Per specificare che la funzionalità o il ruolo deve essere aggiunto, impostare questa proprietà su "Present". Per specificare che la funzionalità o il ruolo venga rimosso, impostare la proprietà su "Absent".</span><span class="sxs-lookup"><span data-stu-id="c797e-117">To ensure that the role or feature is added, set this property to "Present" To ensure that the role or feature is removed, set the property to "Absent".</span></span>| 
| <span data-ttu-id="c797e-118">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="c797e-118">IncludeAllSubFeature</span></span>| <span data-ttu-id="c797e-119">Impostare questa proprietà su __$true__ per specificare lo stato di tutte le funzionalità secondarie necessarie insieme allo stato della funzionalità specificata con la proprietà __Name__.</span><span class="sxs-lookup"><span data-stu-id="c797e-119">Set this property to __$true__ to ensure the state of all required subfeatures with the state of the feature you specify with the __Name__ property.</span></span>| 
| <span data-ttu-id="c797e-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="c797e-120">LogPath</span></span>| <span data-ttu-id="c797e-121">Indica il percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.</span><span class="sxs-lookup"><span data-stu-id="c797e-121">Indicates the path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="c797e-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c797e-122">DependsOn</span></span>| <span data-ttu-id="c797e-123">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="c797e-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c797e-124">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c797e-124">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="c797e-125">Source</span><span class="sxs-lookup"><span data-stu-id="c797e-125">Source</span></span>| <span data-ttu-id="c797e-126">Indica il percorso del file di origine da usare per l'installazione, se necessario.</span><span class="sxs-lookup"><span data-stu-id="c797e-126">Indicates the location of the source file to use for installation, if necessary.</span></span>| 

## <a name="example"></a><span data-ttu-id="c797e-127">Esempio</span><span class="sxs-lookup"><span data-stu-id="c797e-127">Example</span></span>
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```

