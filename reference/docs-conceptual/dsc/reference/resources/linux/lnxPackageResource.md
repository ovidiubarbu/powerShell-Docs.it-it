---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxPackage DSC per Linux
ms.openlocfilehash: 4091cbbd5e34a84b9011870da4bda93281378347
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954818"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="d7b89-103">Risorsa nxPackage DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="d7b89-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="d7b89-104">La risorsa **nxPackage** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i pacchetti in un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="d7b89-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="d7b89-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d7b89-105">Syntax</span></span>

```Syntax
nxPackage <string> #ResourceName
{
    Name = <string>
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ FilePath = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="d7b89-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="d7b89-106">Properties</span></span>

|<span data-ttu-id="d7b89-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="d7b89-107">Property</span></span> |<span data-ttu-id="d7b89-108">Description</span><span class="sxs-lookup"><span data-stu-id="d7b89-108">Description</span></span> |
|---|---|
|<span data-ttu-id="d7b89-109">Nome</span><span class="sxs-lookup"><span data-stu-id="d7b89-109">Name</span></span> |<span data-ttu-id="d7b89-110">Nome del pacchetto per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="d7b89-110">The name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="d7b89-111">PackageManager</span><span class="sxs-lookup"><span data-stu-id="d7b89-111">PackageManager</span></span> |<span data-ttu-id="d7b89-112">I valori supportati sono **yum**, **apt** e **zypper**.</span><span class="sxs-lookup"><span data-stu-id="d7b89-112">Supported values are **yum**, **apt**, and **zypper**.</span></span> <span data-ttu-id="d7b89-113">Specifica lo strumento di gestione dei pacchetti da usare durante l'installazione dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="d7b89-113">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="d7b89-114">Se si specifica **FilePath**, verrà usato il percorso fornito per installare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="d7b89-114">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="d7b89-115">In caso contrario, verrà usato uno strumento di gestione dei pacchetti per installare il pacchetto da un repository preconfigurato.</span><span class="sxs-lookup"><span data-stu-id="d7b89-115">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="d7b89-116">Se non si specifica né **PackageManager** né **FilePath**, viene usato il sistema di gestione dei pacchetti predefinito per il sistema.</span><span class="sxs-lookup"><span data-stu-id="d7b89-116">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span> |
|<span data-ttu-id="d7b89-117">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="d7b89-117">PackageGroup</span></span> |<span data-ttu-id="d7b89-118">Se `$true`, **Name** sarà il nome di un gruppo di pacchetti da usare con **PackageManager**.</span><span class="sxs-lookup"><span data-stu-id="d7b89-118">If `$true`, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="d7b89-119">**PackageGroup** non è un valore valido quando si specifica **FilePath**.</span><span class="sxs-lookup"><span data-stu-id="d7b89-119">**PackageGroup** is not valid when providing a **FilePath**.</span></span> |
|<span data-ttu-id="d7b89-120">Arguments</span><span class="sxs-lookup"><span data-stu-id="d7b89-120">Arguments</span></span> |<span data-ttu-id="d7b89-121">Stringa di argomenti che verrà passata al pacchetto esattamente nel modo specificato.</span><span class="sxs-lookup"><span data-stu-id="d7b89-121">A string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="d7b89-122">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="d7b89-122">ReturnCode</span></span> |<span data-ttu-id="d7b89-123">Codice restituito previsto.</span><span class="sxs-lookup"><span data-stu-id="d7b89-123">The expected return code.</span></span> <span data-ttu-id="d7b89-124">Se l'effettivo codice restituito non corrisponde al valore previsto specificato qui, la configurazione restituirà un errore.</span><span class="sxs-lookup"><span data-stu-id="d7b89-124">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |
|<span data-ttu-id="d7b89-125">FilePath</span><span class="sxs-lookup"><span data-stu-id="d7b89-125">FilePath</span></span> |<span data-ttu-id="d7b89-126">Percorso in cui si trova il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="d7b89-126">The file path where the package resides.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="d7b89-127">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="d7b89-127">Common properties</span></span>

|<span data-ttu-id="d7b89-128">Proprietà</span><span class="sxs-lookup"><span data-stu-id="d7b89-128">Property</span></span> |<span data-ttu-id="d7b89-129">Description</span><span class="sxs-lookup"><span data-stu-id="d7b89-129">Description</span></span> |
|---|---|
|<span data-ttu-id="d7b89-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d7b89-130">DependsOn</span></span> |<span data-ttu-id="d7b89-131">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="d7b89-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d7b89-132">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d7b89-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="d7b89-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="d7b89-133">Ensure</span></span> |<span data-ttu-id="d7b89-134">Determina se verificare l'esistenza del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="d7b89-134">Determines whether to check if the package exists.</span></span> <span data-ttu-id="d7b89-135">Impostare questa proprietà su **Present** per assicurarsi che il pacchetto esista.</span><span class="sxs-lookup"><span data-stu-id="d7b89-135">Set this property to **Present** to ensure the package exists.</span></span> <span data-ttu-id="d7b89-136">Impostarla su **Absent** per assicurarsi che il pacchetto non esista.</span><span class="sxs-lookup"><span data-stu-id="d7b89-136">Set it to **Absent** to ensure the package does not exist.</span></span> <span data-ttu-id="d7b89-137">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="d7b89-137">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="d7b89-138">Esempio</span><span class="sxs-lookup"><span data-stu-id="d7b89-138">Example</span></span>

<span data-ttu-id="d7b89-139">L'esempio seguente specifica che il pacchetto denominato "httpd" è installato in un computer Linux, usando lo strumento di gestione dei pacchetti "Yum".</span><span class="sxs-lookup"><span data-stu-id="d7b89-139">The following example ensures that the package named "httpd" is installed on a Linux computer, using the "Yum" package manager.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxPackage httpd
    {
        Name = "httpd"
        Ensure = "Present"
        PackageManager = "Yum"
    }
}
```