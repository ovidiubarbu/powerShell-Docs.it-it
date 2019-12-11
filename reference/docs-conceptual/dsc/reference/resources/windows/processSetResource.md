---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa ProcessSet DSC
ms.openlocfilehash: 72925d3a9516f5c0040427773a3b1d66034667bb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953128"
---
# <a name="dsc-processset-resource"></a><span data-ttu-id="852fb-103">Risorsa ProcessSet DSC</span><span class="sxs-lookup"><span data-stu-id="852fb-103">DSC ProcessSet Resource</span></span>

> <span data-ttu-id="852fb-104">Si applica a: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="852fb-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="852fb-105">La risorsa **ProcessSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per configurare i processi in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="852fb-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="852fb-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="852fb-106">Syntax</span></span>

```Syntax
ProcessSet [string] #ResourceName
{
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="852fb-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="852fb-107">Properties</span></span>

|<span data-ttu-id="852fb-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="852fb-108">Property</span></span> |<span data-ttu-id="852fb-109">Description</span><span class="sxs-lookup"><span data-stu-id="852fb-109">Description</span></span> |
|---|---|
|<span data-ttu-id="852fb-110">Path</span><span class="sxs-lookup"><span data-stu-id="852fb-110">Path</span></span> |<span data-ttu-id="852fb-111">Percorso dell'eseguibile del processo.</span><span class="sxs-lookup"><span data-stu-id="852fb-111">The path to the process executable.</span></span> <span data-ttu-id="852fb-112">Se questi sono i nomi dei file eseguibili (non i percorsi completi), la risorsa DSC cercherà i file nella variabile `$env:Path` di ambiente.</span><span class="sxs-lookup"><span data-stu-id="852fb-112">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment `$env:Path` variable to find the files.</span></span> <span data-ttu-id="852fb-113">Se i valori di questa proprietà sono percorsi completi, DSC non userà la variabile `$env:Path` di ambiente per individuare i file e genererà un errore in presenza di percorsi non esistenti.</span><span class="sxs-lookup"><span data-stu-id="852fb-113">If the values of this property are fully qualified paths, DSC will not use the `$env:Path` environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="852fb-114">I percorsi relativi non sono consentiti.</span><span class="sxs-lookup"><span data-stu-id="852fb-114">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="852fb-115">Credential</span><span class="sxs-lookup"><span data-stu-id="852fb-115">Credential</span></span> |<span data-ttu-id="852fb-116">Indica le credenziali per l'avvio del processo.</span><span class="sxs-lookup"><span data-stu-id="852fb-116">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="852fb-117">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="852fb-117">StandardErrorPath</span></span> |<span data-ttu-id="852fb-118">Percorso in cui i processi scrivono l'errore standard.</span><span class="sxs-lookup"><span data-stu-id="852fb-118">The path to which the processes write standard error.</span></span> <span data-ttu-id="852fb-119">Qualsiasi file esistente verrà sovrascritto.</span><span class="sxs-lookup"><span data-stu-id="852fb-119">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="852fb-120">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="852fb-120">StandardInputPath</span></span> |<span data-ttu-id="852fb-121">Flusso da cui il processo riceve l'input standard.</span><span class="sxs-lookup"><span data-stu-id="852fb-121">The stream from which the process receives standard input.</span></span> |
|<span data-ttu-id="852fb-122">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="852fb-122">StandardOutputPath</span></span> |<span data-ttu-id="852fb-123">Percorso del file in cui i processi scrivono l'output standard.</span><span class="sxs-lookup"><span data-stu-id="852fb-123">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="852fb-124">Qualsiasi file esistente verrà sovrascritto.</span><span class="sxs-lookup"><span data-stu-id="852fb-124">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="852fb-125">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="852fb-125">WorkingDirectory</span></span> |<span data-ttu-id="852fb-126">Percorso usato come directory di lavoro corrente per i processi.</span><span class="sxs-lookup"><span data-stu-id="852fb-126">The location used as the current working directory for the processes.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="852fb-127">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="852fb-127">Common properties</span></span>

|<span data-ttu-id="852fb-128">Proprietà</span><span class="sxs-lookup"><span data-stu-id="852fb-128">Property</span></span> |<span data-ttu-id="852fb-129">Description</span><span class="sxs-lookup"><span data-stu-id="852fb-129">Description</span></span> |
|---|---|
|<span data-ttu-id="852fb-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="852fb-130">DependsOn</span></span> |<span data-ttu-id="852fb-131">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="852fb-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="852fb-132">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="852fb-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="852fb-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="852fb-133">Ensure</span></span> |<span data-ttu-id="852fb-134">Specifica se il processo esiste.</span><span class="sxs-lookup"><span data-stu-id="852fb-134">Specifies whether the processes exists.</span></span> <span data-ttu-id="852fb-135">Impostare questa proprietà su **Present** per specificare che il processo esiste.</span><span class="sxs-lookup"><span data-stu-id="852fb-135">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="852fb-136">In caso contrario, impostarla su **Absent**.</span><span class="sxs-lookup"><span data-stu-id="852fb-136">Otherwise, set it to **Absent**.</span></span> <span data-ttu-id="852fb-137">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="852fb-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="852fb-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="852fb-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="852fb-139">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="852fb-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="852fb-140">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="852fb-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="852fb-141">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="852fb-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>