---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa ProcessSet DSC
ms.openlocfilehash: 412cf1076996126f0d9b7a9a8ebbc9bdb7ecf377
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189925"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="bd352-103">Risorsa WindowsProcess DSC</span><span class="sxs-lookup"><span data-stu-id="bd352-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="bd352-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bd352-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="bd352-105">La risorsa **ProcessSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per configurare i processi in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="bd352-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="bd352-106">Questa risorsa è una [risorsa composta](authoringResourceComposite.md) che chiama la [risorsa WindowsProcess](windowsProcessResource.md) per ogni gruppo specificato nel parametro `GroupName`.</span><span class="sxs-lookup"><span data-stu-id="bd352-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="bd352-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bd352-107">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="bd352-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="bd352-108">Properties</span></span>
|  <span data-ttu-id="bd352-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="bd352-109">Property</span></span>  |  <span data-ttu-id="bd352-110">Description</span><span class="sxs-lookup"><span data-stu-id="bd352-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="bd352-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="bd352-111">Arguments</span></span>| <span data-ttu-id="bd352-112">Stringa che contiene argomenti da passare al processo così come è.</span><span class="sxs-lookup"><span data-stu-id="bd352-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="bd352-113">Se è necessario passare più argomenti, inserirli tutti in questa stringa.</span><span class="sxs-lookup"><span data-stu-id="bd352-113">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="bd352-114">Path</span><span class="sxs-lookup"><span data-stu-id="bd352-114">Path</span></span>| <span data-ttu-id="bd352-115">Percorsi degli eseguibili del processo.</span><span class="sxs-lookup"><span data-stu-id="bd352-115">The paths to the process executables.</span></span> <span data-ttu-id="bd352-116">Se questi sono i nomi dei file eseguibili (non i percorsi completi), la risorsa DSC cercherà i file nella variabile **Path** di ambiente (`$env:Path`).</span><span class="sxs-lookup"><span data-stu-id="bd352-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="bd352-117">Se i valori di questa proprietà sono percorsi completi, DSC non userà la variabile **Path** di ambiente per individuare i file e genererà un errore se il percorso non esiste.</span><span class="sxs-lookup"><span data-stu-id="bd352-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="bd352-118">I percorsi relativi non sono consentiti.</span><span class="sxs-lookup"><span data-stu-id="bd352-118">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="bd352-119">Credential</span><span class="sxs-lookup"><span data-stu-id="bd352-119">Credential</span></span>| <span data-ttu-id="bd352-120">Indica le credenziali per l'avvio del processo.</span><span class="sxs-lookup"><span data-stu-id="bd352-120">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="bd352-121">Ensure</span><span class="sxs-lookup"><span data-stu-id="bd352-121">Ensure</span></span>| <span data-ttu-id="bd352-122">Specifica se il processo esiste.</span><span class="sxs-lookup"><span data-stu-id="bd352-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="bd352-123">Impostare questa proprietà su "Present" per specificare che il processo esiste.</span><span class="sxs-lookup"><span data-stu-id="bd352-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="bd352-124">In caso contrario, impostarla su "Absent".</span><span class="sxs-lookup"><span data-stu-id="bd352-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="bd352-125">Il valore predefinito è "Present".</span><span class="sxs-lookup"><span data-stu-id="bd352-125">The default is "Present".</span></span>|
| <span data-ttu-id="bd352-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="bd352-126">StandardErrorPath</span></span>| <span data-ttu-id="bd352-127">Percorso in cui i processi scrivono l'errore standard.</span><span class="sxs-lookup"><span data-stu-id="bd352-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="bd352-128">Qualsiasi file esistente verrà sovrascritto.</span><span class="sxs-lookup"><span data-stu-id="bd352-128">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="bd352-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="bd352-129">StandardInputPath</span></span>| <span data-ttu-id="bd352-130">Flusso da cui il processo riceve l'input standard.</span><span class="sxs-lookup"><span data-stu-id="bd352-130">The stream from which the process receives standard input.</span></span>|
| <span data-ttu-id="bd352-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="bd352-131">StandardOutputPath</span></span>| <span data-ttu-id="bd352-132">Percorso del file in cui i processi scrivono l'output standard.</span><span class="sxs-lookup"><span data-stu-id="bd352-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="bd352-133">Qualsiasi file esistente verrà sovrascritto.</span><span class="sxs-lookup"><span data-stu-id="bd352-133">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="bd352-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="bd352-134">WorkingDirectory</span></span>| <span data-ttu-id="bd352-135">Percorso usato come directory di lavoro corrente per i processi.</span><span class="sxs-lookup"><span data-stu-id="bd352-135">The location used as the current working directory for the processes.</span></span>|
| <span data-ttu-id="bd352-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="bd352-136">DependsOn</span></span> | <span data-ttu-id="bd352-137">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="bd352-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bd352-138">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **_ResourceType**, la sintassi per usare questa proprietà è 'DependsOn = "[ResourceType]ResourceName"''.</span><span class="sxs-lookup"><span data-stu-id="bd352-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>|