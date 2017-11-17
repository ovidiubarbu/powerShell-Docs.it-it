---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Risorsa nxScript DSC per Linux
ms.openlocfilehash: 381d8d214654641a34eeebcb54a81a25d61ee644
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="33b98-103">Risorsa nxScript DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="33b98-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="33b98-104">La risorsa **nxScript** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per eseguire script Linux in un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="33b98-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="33b98-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="33b98-105">Syntax</span></span>

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    { Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="33b98-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="33b98-106">Properties</span></span>

|  <span data-ttu-id="33b98-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="33b98-107">Property</span></span> |  <span data-ttu-id="33b98-108">Descrizione</span><span class="sxs-lookup"><span data-stu-id="33b98-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="33b98-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="33b98-109">GetScript</span></span>| <span data-ttu-id="33b98-110">Fornisce uno script eseguito quando si richiama il cmdlet [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx).</span><span class="sxs-lookup"><span data-stu-id="33b98-110">Provides a script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span></span> <span data-ttu-id="33b98-111">Lo script deve iniziare con una sequenza di caratteri shebang, ad esempio #!/bin/bash.</span><span class="sxs-lookup"><span data-stu-id="33b98-111">The script must begin with a shebang, such as #!/bin/bash.</span></span>| 
| <span data-ttu-id="33b98-112">SetScript</span><span class="sxs-lookup"><span data-stu-id="33b98-112">SetScript</span></span>| <span data-ttu-id="33b98-113">Fornisce uno script.</span><span class="sxs-lookup"><span data-stu-id="33b98-113">Provides a script.</span></span> <span data-ttu-id="33b98-114">Quando si richiama il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), viene eseguito per primo il blocco **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="33b98-114">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** runs first.</span></span> <span data-ttu-id="33b98-115">Se il blocco **TestScript** restituisce un codice di uscita diverso da 0, il blocco **SetScript** viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="33b98-115">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="33b98-116">Se **TestScript** restituisce un codice di uscita uguale a 0, il blocco **SetScript** non viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="33b98-116">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="33b98-117">Lo script deve iniziare con una sequenza di caratteri shebang, ad esempio `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="33b98-117">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>| 
| <span data-ttu-id="33b98-118">TestScript</span><span class="sxs-lookup"><span data-stu-id="33b98-118">TestScript</span></span>| <span data-ttu-id="33b98-119">Fornisce uno script.</span><span class="sxs-lookup"><span data-stu-id="33b98-119">Provides a script.</span></span> <span data-ttu-id="33b98-120">Quando si richiama il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), questo script viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="33b98-120">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this script runs.</span></span> <span data-ttu-id="33b98-121">Se restituisce un codice di uscita diverso da 0, il blocco SetScript viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="33b98-121">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="33b98-122">Se restituisce un codice di uscita uguale a 0, il blocco **SetScript** non viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="33b98-122">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="33b98-123">**TestScript** viene eseguito anche quando si richiama il cmdlet [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx).</span><span class="sxs-lookup"><span data-stu-id="33b98-123">The **TestScript** also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="33b98-124">In questo caso, tuttavia, il blocco **SetScript** non viene eseguito, indipendentemente dal codice di uscita restituito da **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="33b98-124">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="33b98-125">**TestScript** deve restituire un codice di uscita uguale a 0 se l'effettiva configurazione corrisponde alla configurazione dello stato desiderato corrente e un codice di uscita diverso da 0 in caso contrario.</span><span class="sxs-lookup"><span data-stu-id="33b98-125">The **TestScript** must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="33b98-126">La configurazione dello stato desiderato corrente è l'ultima configurazione applicata al nodo che usa DSC.</span><span class="sxs-lookup"><span data-stu-id="33b98-126">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="33b98-127">Lo script deve iniziare con una sequenza di caratteri shebang, ad esempio 1#!/bin/bash.1</span><span class="sxs-lookup"><span data-stu-id="33b98-127">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>| 
| <span data-ttu-id="33b98-128">User</span><span class="sxs-lookup"><span data-stu-id="33b98-128">User</span></span>| <span data-ttu-id="33b98-129">Utente per l'esecuzione dello script.</span><span class="sxs-lookup"><span data-stu-id="33b98-129">The user to run the script as.</span></span>| 
| <span data-ttu-id="33b98-130">Group</span><span class="sxs-lookup"><span data-stu-id="33b98-130">Group</span></span>| <span data-ttu-id="33b98-131">Gruppo per l'esecuzione dello script.</span><span class="sxs-lookup"><span data-stu-id="33b98-131">The group to run the script as.</span></span>| 
| <span data-ttu-id="33b98-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="33b98-132">DependsOn</span></span> | <span data-ttu-id="33b98-133">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="33b98-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="33b98-134">Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="33b98-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="33b98-135">Esempio</span><span class="sxs-lookup"><span data-stu-id="33b98-135">Example</span></span>

<span data-ttu-id="33b98-136">L'esempio seguente illustra l'uso della risorsa **nxScript** per eseguire attività aggiuntive di gestione della configurazione.</span><span class="sxs-lookup"><span data-stu-id="33b98-136">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```
Import-DSCResource -Module nx 

Node $node {
nxScript KeepDirEmpty{

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

