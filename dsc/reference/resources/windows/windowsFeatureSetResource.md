---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsFeatureSet DSC
ms.openlocfilehash: 8a64168d9ad0d6a6c40eb0398cc734fa93a247dc
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726780"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="d2739-103">Risorsa WindowsFeatureSet DSC</span><span class="sxs-lookup"><span data-stu-id="d2739-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="d2739-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d2739-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d2739-105">La risorsa **WindowsFeatureSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare le funzionalità e i ruoli aggiunti in un nodo di destinazione o rimossi da quest'ultimo.</span><span class="sxs-lookup"><span data-stu-id="d2739-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>
<span data-ttu-id="d2739-106">Questa risorsa è una [risorsa composta](../../../resources/authoringResourceComposite.md) che chiama la [risorsa WindowsFeature](windowsfeatureResource.md) per ogni funzionalità specificata nella proprietà `Name`.</span><span class="sxs-lookup"><span data-stu-id="d2739-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="d2739-107">Usare questa risorsa quando si vogliono configurare diverse istanze di WindowsFeature nello stesso stato.</span><span class="sxs-lookup"><span data-stu-id="d2739-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2739-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d2739-108">Syntax</span></span>

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="d2739-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="d2739-109">Properties</span></span>

|  <span data-ttu-id="d2739-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="d2739-110">Property</span></span>  |  <span data-ttu-id="d2739-111">Description</span><span class="sxs-lookup"><span data-stu-id="d2739-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="d2739-112">Nome</span><span class="sxs-lookup"><span data-stu-id="d2739-112">Name</span></span>| <span data-ttu-id="d2739-113">Nomi dei ruoli o delle funzionalità che si vogliono aggiungere o rimuovere.</span><span class="sxs-lookup"><span data-stu-id="d2739-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="d2739-114">Corrisponde alla proprietà **Name** del cmdlet [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) e non al nome visualizzato dei ruoli o delle funzionalità.</span><span class="sxs-lookup"><span data-stu-id="d2739-114">This is the same as the **Name** property of the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) cmdlet, and not the display name of the roles or features.</span></span>|
| <span data-ttu-id="d2739-115">Credential</span><span class="sxs-lookup"><span data-stu-id="d2739-115">Credential</span></span>| <span data-ttu-id="d2739-116">Credenziali da usare per aggiungere o rimuovere i ruoli o le funzionalità.</span><span class="sxs-lookup"><span data-stu-id="d2739-116">The credentials to use to add or remove the roles or features.</span></span>|
| <span data-ttu-id="d2739-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="d2739-117">Ensure</span></span>| <span data-ttu-id="d2739-118">Indica se i ruoli o le funzionalità vengono aggiunte.</span><span class="sxs-lookup"><span data-stu-id="d2739-118">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="d2739-119">Per specificare che i ruoli o le funzionalità devono essere aggiunte, impostare questa proprietà su "Present". Per specificare che i ruoli o le funzionalità devono essere rimosse, impostare la proprietà su "Absent".</span><span class="sxs-lookup"><span data-stu-id="d2739-119">To ensure that the roles or features are added, set this property to "Present" To ensure that the roles or features are removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="d2739-120">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="d2739-120">IncludeAllSubFeature</span></span>| <span data-ttu-id="d2739-121">Impostare questa proprietà su **$true** per specificare tutte le funzionalità secondarie necessarie insieme alla funzionalità specificata con la proprietà **Name**.</span><span class="sxs-lookup"><span data-stu-id="d2739-121">Set this property to **$true** to include all required subfeatures with of the features you specify with the **Name** property.</span></span>|
| <span data-ttu-id="d2739-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="d2739-122">LogPath</span></span>| <span data-ttu-id="d2739-123">Percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.</span><span class="sxs-lookup"><span data-stu-id="d2739-123">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="d2739-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d2739-124">DependsOn</span></span>| <span data-ttu-id="d2739-125">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="d2739-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d2739-126">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d2739-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="d2739-127">Source</span><span class="sxs-lookup"><span data-stu-id="d2739-127">Source</span></span>| <span data-ttu-id="d2739-128">Indica il percorso del file di origine da usare per l'installazione, se necessario.</span><span class="sxs-lookup"><span data-stu-id="d2739-128">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="d2739-129">Esempio</span><span class="sxs-lookup"><span data-stu-id="d2739-129">Example</span></span>

<span data-ttu-id="d2739-130">La configurazione seguente garantisce che siano installate tutte le funzionalità e le funzionalità secondarie del **server Web** (IIS) e del **server SMTP**.</span><span class="sxs-lookup"><span data-stu-id="d2739-130">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

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
