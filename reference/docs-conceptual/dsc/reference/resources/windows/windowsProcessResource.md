---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsProcess DSC
ms.openlocfilehash: e168cdebb04f7ec83b73a537a5f188299f40d8b7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952838"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="2de72-103">Risorsa WindowsProcess DSC</span><span class="sxs-lookup"><span data-stu-id="2de72-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="2de72-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="2de72-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="2de72-105">La risorsa **WindowsProcess** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per configurare i processi in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="2de72-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="2de72-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2de72-106">Syntax</span></span>

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="2de72-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="2de72-107">Properties</span></span>

|<span data-ttu-id="2de72-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="2de72-108">Property</span></span> |<span data-ttu-id="2de72-109">Description</span><span class="sxs-lookup"><span data-stu-id="2de72-109">Description</span></span> |
|---|---|
|<span data-ttu-id="2de72-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="2de72-110">Arguments</span></span> |<span data-ttu-id="2de72-111">Indica una stringa di argomenti da passare al processo come è.</span><span class="sxs-lookup"><span data-stu-id="2de72-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="2de72-112">Se è necessario passare più argomenti, inserirli tutti in questa stringa.</span><span class="sxs-lookup"><span data-stu-id="2de72-112">If you need to pass several arguments, put them all in this string.</span></span> |
|<span data-ttu-id="2de72-113">Path</span><span class="sxs-lookup"><span data-stu-id="2de72-113">Path</span></span> |<span data-ttu-id="2de72-114">Percorso dell'eseguibile del processo.</span><span class="sxs-lookup"><span data-stu-id="2de72-114">The path to the process executable.</span></span> <span data-ttu-id="2de72-115">Se è il nome del file eseguibile (non il percorso completo), la risorsa DSC cercherà il file eseguibile nella variabile `$env:Path` di ambiente.</span><span class="sxs-lookup"><span data-stu-id="2de72-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment `$env:Path` variable to find the executable file.</span></span> <span data-ttu-id="2de72-116">Se il valore di questa proprietà è un percorso completo, DSC non userà la variabile `$env:Path` per individuare il file e genererà un errore se il percorso non esiste.</span><span class="sxs-lookup"><span data-stu-id="2de72-116">If the value of this property is a fully qualified path, DSC will not use the `$env:Path` variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="2de72-117">I percorsi relativi non sono consentiti.</span><span class="sxs-lookup"><span data-stu-id="2de72-117">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="2de72-118">Credential</span><span class="sxs-lookup"><span data-stu-id="2de72-118">Credential</span></span> |<span data-ttu-id="2de72-119">Indica le credenziali per l'avvio del processo.</span><span class="sxs-lookup"><span data-stu-id="2de72-119">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="2de72-120">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="2de72-120">StandardErrorPath</span></span> |<span data-ttu-id="2de72-121">Indica il percorso della directory in cui scrivere l'errore standard.</span><span class="sxs-lookup"><span data-stu-id="2de72-121">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="2de72-122">Qualsiasi file esistente verrà sovrascritto.</span><span class="sxs-lookup"><span data-stu-id="2de72-122">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="2de72-123">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="2de72-123">StandardInputPath</span></span> |<span data-ttu-id="2de72-124">Indica il percorso di input standard.</span><span class="sxs-lookup"><span data-stu-id="2de72-124">Indicates the standard input location.</span></span> |
|<span data-ttu-id="2de72-125">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="2de72-125">StandardOutputPath</span></span> |<span data-ttu-id="2de72-126">Indica il percorso in cui scrivere l'output standard.</span><span class="sxs-lookup"><span data-stu-id="2de72-126">Indicates the location to write the standard output.</span></span> <span data-ttu-id="2de72-127">Qualsiasi file esistente verrà sovrascritto.</span><span class="sxs-lookup"><span data-stu-id="2de72-127">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="2de72-128">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="2de72-128">WorkingDirectory</span></span> |<span data-ttu-id="2de72-129">Indica il percorso che verrà usato come directory di lavoro corrente per il processo.</span><span class="sxs-lookup"><span data-stu-id="2de72-129">Indicates the location that will be used as the current working directory for the process.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="2de72-130">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="2de72-130">Common properties</span></span>

|<span data-ttu-id="2de72-131">Proprietà</span><span class="sxs-lookup"><span data-stu-id="2de72-131">Property</span></span> |<span data-ttu-id="2de72-132">Description</span><span class="sxs-lookup"><span data-stu-id="2de72-132">Description</span></span> |
|---|---|
|<span data-ttu-id="2de72-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2de72-133">DependsOn</span></span> |<span data-ttu-id="2de72-134">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="2de72-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2de72-135">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="2de72-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="2de72-136">Ensure</span><span class="sxs-lookup"><span data-stu-id="2de72-136">Ensure</span></span> |<span data-ttu-id="2de72-137">Indica se il processo esiste.</span><span class="sxs-lookup"><span data-stu-id="2de72-137">Indicates if the process exists.</span></span> <span data-ttu-id="2de72-138">Impostare questa proprietà su **Present** per specificare che il processo esiste.</span><span class="sxs-lookup"><span data-stu-id="2de72-138">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="2de72-139">In caso contrario, impostarla su **Absent**.</span><span class="sxs-lookup"><span data-stu-id="2de72-139">Otherwise, set it to **Absent**.</span></span> <span data-ttu-id="2de72-140">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="2de72-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="2de72-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="2de72-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="2de72-142">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="2de72-142">Sets the credential for running the entire resource as.</span></span> |