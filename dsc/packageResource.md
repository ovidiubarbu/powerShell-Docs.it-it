---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Package DSC
ms.openlocfilehash: 3046ba7d57776a996a0b917348a0e863db6cd0c8
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093804"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="acf9a-103">Risorsa Package DSC</span><span class="sxs-lookup"><span data-stu-id="acf9a-103">DSC Package Resource</span></span>

> <span data-ttu-id="acf9a-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="acf9a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="acf9a-105">La risorsa **Package** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per installare o disinstallare pacchetti, ad esempio i pacchetti di Windows Installer e setup.exe, nei nodi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="acf9a-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="acf9a-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="acf9a-106">Syntax</span></span>

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="acf9a-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="acf9a-107">Properties</span></span>

|  <span data-ttu-id="acf9a-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="acf9a-108">Property</span></span>  |  <span data-ttu-id="acf9a-109">Description</span><span class="sxs-lookup"><span data-stu-id="acf9a-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="acf9a-110">Nome</span><span class="sxs-lookup"><span data-stu-id="acf9a-110">Name</span></span>| <span data-ttu-id="acf9a-111">Indica il nome del pacchetto per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="acf9a-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="acf9a-112">Path</span><span class="sxs-lookup"><span data-stu-id="acf9a-112">Path</span></span>| <span data-ttu-id="acf9a-113">Percorso in cui si trova il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="acf9a-113">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="acf9a-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="acf9a-114">ProductId</span></span>| <span data-ttu-id="acf9a-115">Indica l'ID prodotto che identifica in modo univoco il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="acf9a-115">Indicates the product ID that uniquely identifies the package.</span></span>|
| <span data-ttu-id="acf9a-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="acf9a-116">Arguments</span></span>| <span data-ttu-id="acf9a-117">Elenca una stringa di argomenti che verrà passata al pacchetto esattamente nel modo specificato.</span><span class="sxs-lookup"><span data-stu-id="acf9a-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="acf9a-118">Credential</span><span class="sxs-lookup"><span data-stu-id="acf9a-118">Credential</span></span>| <span data-ttu-id="acf9a-119">Fornisce l'accesso al pacchetto in un'origine remota.</span><span class="sxs-lookup"><span data-stu-id="acf9a-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="acf9a-120">Questa proprietà non viene usata per installare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="acf9a-120">This property is not used to install the package.</span></span> <span data-ttu-id="acf9a-121">Il pacchetto viene sempre installato nel sistema locale.</span><span class="sxs-lookup"><span data-stu-id="acf9a-121">The package is always installed on the local system.</span></span>|
| <span data-ttu-id="acf9a-122">Ensure</span><span class="sxs-lookup"><span data-stu-id="acf9a-122">Ensure</span></span>| <span data-ttu-id="acf9a-123">Indica se il pacchetto è installato.</span><span class="sxs-lookup"><span data-stu-id="acf9a-123">Indicates if the package is installed.</span></span> <span data-ttu-id="acf9a-124">Impostare questa proprietà su "Absent" per specificare che il pacchetto non è installato (o disinstallare il pacchetto se è installato).</span><span class="sxs-lookup"><span data-stu-id="acf9a-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="acf9a-125">Impostarla su "Present" (valore predefinito) per specificare che il pacchetto è installato.</span><span class="sxs-lookup"><span data-stu-id="acf9a-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="acf9a-126">LogPath</span><span class="sxs-lookup"><span data-stu-id="acf9a-126">LogPath</span></span>| <span data-ttu-id="acf9a-127">Indica il percorso completo in cui il provider deve salvare un file di log per installare o disinstallare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="acf9a-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="acf9a-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="acf9a-128">DependsOn</span></span> | <span data-ttu-id="acf9a-129">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="acf9a-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="acf9a-130">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è \`DependsOn = "[ResourceType]ResourceName"\`\`.</span><span class="sxs-lookup"><span data-stu-id="acf9a-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|
| <span data-ttu-id="acf9a-131">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="acf9a-131">ReturnCode</span></span>| <span data-ttu-id="acf9a-132">Indica il codice restituito previsto.</span><span class="sxs-lookup"><span data-stu-id="acf9a-132">Indicates the expected return code.</span></span> <span data-ttu-id="acf9a-133">Se l'effettivo codice restituito non corrisponde al valore previsto specificato qui, la configurazione restituirà un errore.</span><span class="sxs-lookup"><span data-stu-id="acf9a-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|

## <a name="example"></a><span data-ttu-id="acf9a-134">Esempio</span><span class="sxs-lookup"><span data-stu-id="acf9a-134">Example</span></span>

<span data-ttu-id="acf9a-135">Questo esempio esegue il programma di installazione MSI che si trova nel percorso specificato e che ha l'ID prodotto indicato.</span><span class="sxs-lookup"><span data-stu-id="acf9a-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```