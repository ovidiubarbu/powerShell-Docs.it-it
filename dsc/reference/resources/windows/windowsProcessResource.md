---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsProcess DSC
ms.openlocfilehash: cee93ab283ded407d6e032161125aa6d6ac98827
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076770"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="edf29-103">Risorsa WindowsProcess DSC</span><span class="sxs-lookup"><span data-stu-id="edf29-103">DSC WindowsProcess Resource</span></span>

<span data-ttu-id="edf29-104">_Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="edf29-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="edf29-105">La risorsa **WindowsProcess** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per configurare i processi in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="edf29-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="edf29-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="edf29-106">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="edf29-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="edf29-107">Properties</span></span>

| <span data-ttu-id="edf29-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="edf29-108">Property</span></span> | <span data-ttu-id="edf29-109">Description</span><span class="sxs-lookup"><span data-stu-id="edf29-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="edf29-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="edf29-110">Arguments</span></span>| <span data-ttu-id="edf29-111">Indica una stringa di argomenti da passare al processo come è.</span><span class="sxs-lookup"><span data-stu-id="edf29-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="edf29-112">Se è necessario passare più argomenti, inserirli tutti in questa stringa.</span><span class="sxs-lookup"><span data-stu-id="edf29-112">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="edf29-113">Path</span><span class="sxs-lookup"><span data-stu-id="edf29-113">Path</span></span>| <span data-ttu-id="edf29-114">Percorso dell'eseguibile del processo.</span><span class="sxs-lookup"><span data-stu-id="edf29-114">The path to the process executable.</span></span> <span data-ttu-id="edf29-115">Se è il nome del file eseguibile (non il percorso completo), la risorsa DSC cercherà il file eseguibile nella variabile **Path** di ambiente (`$env:Path`).</span><span class="sxs-lookup"><span data-stu-id="edf29-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="edf29-116">Se il valore di questa proprietà è un percorso completo, DSC non userà la variabile **Path** di ambiente per individuare il file e genererà un errore se il percorso non esiste.</span><span class="sxs-lookup"><span data-stu-id="edf29-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="edf29-117">I percorsi relativi non sono consentiti.</span><span class="sxs-lookup"><span data-stu-id="edf29-117">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="edf29-118">Credential</span><span class="sxs-lookup"><span data-stu-id="edf29-118">Credential</span></span>| <span data-ttu-id="edf29-119">Indica le credenziali per l'avvio del processo.</span><span class="sxs-lookup"><span data-stu-id="edf29-119">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="edf29-120">Ensure</span><span class="sxs-lookup"><span data-stu-id="edf29-120">Ensure</span></span>| <span data-ttu-id="edf29-121">Indica se il processo esiste.</span><span class="sxs-lookup"><span data-stu-id="edf29-121">Indicates if the process exists.</span></span> <span data-ttu-id="edf29-122">Impostare questa proprietà su "Present" per specificare che il processo esiste.</span><span class="sxs-lookup"><span data-stu-id="edf29-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="edf29-123">In caso contrario, impostarla su "Absent".</span><span class="sxs-lookup"><span data-stu-id="edf29-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="edf29-124">Il valore predefinito è "Present".</span><span class="sxs-lookup"><span data-stu-id="edf29-124">The default is "Present".</span></span>|
| <span data-ttu-id="edf29-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="edf29-125">DependsOn</span></span> | <span data-ttu-id="edf29-126">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="edf29-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="edf29-127">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="edf29-127">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"` .</span></span>|
| <span data-ttu-id="edf29-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="edf29-128">StandardErrorPath</span></span>| <span data-ttu-id="edf29-129">Indica il percorso della directory in cui scrivere l'errore standard.</span><span class="sxs-lookup"><span data-stu-id="edf29-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="edf29-130">Qualsiasi file esistente verrà sovrascritto.</span><span class="sxs-lookup"><span data-stu-id="edf29-130">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="edf29-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="edf29-131">StandardInputPath</span></span>| <span data-ttu-id="edf29-132">Indica il percorso di input standard.</span><span class="sxs-lookup"><span data-stu-id="edf29-132">Indicates the standard input location.</span></span>|
| <span data-ttu-id="edf29-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="edf29-133">StandardOutputPath</span></span>| <span data-ttu-id="edf29-134">Indica il percorso in cui scrivere l'output standard.</span><span class="sxs-lookup"><span data-stu-id="edf29-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="edf29-135">Qualsiasi file esistente verrà sovrascritto.</span><span class="sxs-lookup"><span data-stu-id="edf29-135">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="edf29-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="edf29-136">WorkingDirectory</span></span>| <span data-ttu-id="edf29-137">Indica il percorso che verrà usato come directory di lavoro corrente per il processo.</span><span class="sxs-lookup"><span data-stu-id="edf29-137">Indicates the location that will be used as the current working directory for the process.</span></span>|