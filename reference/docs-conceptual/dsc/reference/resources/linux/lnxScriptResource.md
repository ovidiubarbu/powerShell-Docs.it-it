---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxScript DSC per Linux
ms.openlocfilehash: a7f2114aba47bb581cdd19168e784b79dfc5b6ad
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953188"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="ba5f6-103">Risorsa nxScript DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="ba5f6-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="ba5f6-104">La risorsa **nxScript** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per eseguire script Linux in un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="ba5f6-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ba5f6-105">Syntax</span></span>

```Syntax
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="ba5f6-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="ba5f6-106">Properties</span></span>

|<span data-ttu-id="ba5f6-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="ba5f6-107">Property</span></span> |<span data-ttu-id="ba5f6-108">Description</span><span class="sxs-lookup"><span data-stu-id="ba5f6-108">Description</span></span> |
|---|---|
|<span data-ttu-id="ba5f6-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="ba5f6-109">GetScript</span></span> |<span data-ttu-id="ba5f6-110">Fornisce uno script per restituire lo stato corrente del computer.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-110">Provides a script to return current status of the machine.</span></span> <span data-ttu-id="ba5f6-111">Questo script viene eseguito quando si richiama lo script [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer).</span><span class="sxs-lookup"><span data-stu-id="ba5f6-111">This script runs when you invoke the [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="ba5f6-112">Lo script deve iniziare con una sequenza di caratteri shebang, ad esempio `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-112">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="ba5f6-113">SetScript</span><span class="sxs-lookup"><span data-stu-id="ba5f6-113">SetScript</span></span> |<span data-ttu-id="ba5f6-114">Fornisce uno script che attiva lo stato corretto per il computer.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-114">Provides a script that puts the machine in the correct state.</span></span> <span data-ttu-id="ba5f6-115">Quando si richiama lo script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer), viene eseguito per primo **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-115">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, the **TestScript** runs first.</span></span> <span data-ttu-id="ba5f6-116">Se il blocco **TestScript** restituisce un codice di uscita diverso da 0, il blocco **SetScript** viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-116">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="ba5f6-117">Se **TestScript** restituisce un codice di uscita uguale a 0, il blocco **SetScript** non viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-117">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="ba5f6-118">Lo script deve iniziare con una sequenza di caratteri shebang, ad esempio `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-118">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="ba5f6-119">TestScript</span><span class="sxs-lookup"><span data-stu-id="ba5f6-119">TestScript</span></span> |<span data-ttu-id="ba5f6-120">Fornisce uno script che valuta se il nodo si trova attualmente nello stato corretto.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-120">Provides a script that evaluates whether the node is currently in the correct state.</span></span> <span data-ttu-id="ba5f6-121">Quando si richiama lo script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer), questo script viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-121">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, this script runs.</span></span> <span data-ttu-id="ba5f6-122">Se restituisce un codice di uscita diverso da 0, verrà eseguito **SetScript**.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-122">If it returns an exit code other than 0, the **SetScript** will run.</span></span> <span data-ttu-id="ba5f6-123">Se restituisce un codice di uscita uguale a 0, il blocco **SetScript** non viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-123">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="ba5f6-124">**TestScript** viene eseguito anche quando si richiama lo script [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer).</span><span class="sxs-lookup"><span data-stu-id="ba5f6-124">The **TestScript** also runs when you invoke the [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="ba5f6-125">In questo caso, tuttavia, il blocco **SetScript** non viene eseguito, indipendentemente dal codice di uscita restituito da **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-125">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="ba5f6-126">**TestScript** deve includere contenuto e restituire un codice di uscita uguale a 0 se la configurazione effettiva corrisponde alla configurazione dello stato desiderato corrente e un codice di uscita diverso da 0 in caso contrario.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-126">The **TestScript** must contain content and must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="ba5f6-127">La configurazione dello stato desiderato corrente è l'ultima configurazione applicata nel nodo che usa DSC.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-127">The current desired state configuration is the last configuration enacted on the node that is using DSC.</span></span> <span data-ttu-id="ba5f6-128">Lo script deve iniziare con una sequenza di caratteri shebang, ad esempio `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-128">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="ba5f6-129">User</span><span class="sxs-lookup"><span data-stu-id="ba5f6-129">User</span></span> |<span data-ttu-id="ba5f6-130">Utente per l'esecuzione dello script.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-130">The user to run the script as.</span></span> |
|<span data-ttu-id="ba5f6-131">Group</span><span class="sxs-lookup"><span data-stu-id="ba5f6-131">Group</span></span> |<span data-ttu-id="ba5f6-132">Gruppo per l'esecuzione dello script.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-132">The group to run the script as.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="ba5f6-133">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="ba5f6-133">Common properties</span></span>

|<span data-ttu-id="ba5f6-134">Proprietà</span><span class="sxs-lookup"><span data-stu-id="ba5f6-134">Property</span></span> |<span data-ttu-id="ba5f6-135">Description</span><span class="sxs-lookup"><span data-stu-id="ba5f6-135">Description</span></span> |
|---|---|
|<span data-ttu-id="ba5f6-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ba5f6-136">DependsOn</span></span> |<span data-ttu-id="ba5f6-137">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ba5f6-138">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-138">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="ba5f6-139">Esempio</span><span class="sxs-lookup"><span data-stu-id="ba5f6-139">Example</span></span>

<span data-ttu-id="ba5f6-140">L'esempio seguente illustra l'uso della risorsa **nxScript** per eseguire attività aggiuntive di gestione della configurazione.</span><span class="sxs-lookup"><span data-stu-id="ba5f6-140">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxScript KeepDirEmpty {

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
    }
}
```
