---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Package DSC
ms.openlocfilehash: 9285df71a303c9a53dd50d450272575a64e962e7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077195"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="b4979-103">Risorsa Package DSC</span><span class="sxs-lookup"><span data-stu-id="b4979-103">DSC Package Resource</span></span>

<span data-ttu-id="b4979-104">_Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="b4979-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="b4979-105">La risorsa **Package** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per installare o disinstallare pacchetti, ad esempio i pacchetti di Windows Installer e setup.exe, nei nodi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b4979-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="b4979-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b4979-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="b4979-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="b4979-107">Properties</span></span>

| <span data-ttu-id="b4979-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="b4979-108">Property</span></span> | <span data-ttu-id="b4979-109">Description</span><span class="sxs-lookup"><span data-stu-id="b4979-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b4979-110">Nome</span><span class="sxs-lookup"><span data-stu-id="b4979-110">Name</span></span>| <span data-ttu-id="b4979-111">Indica il nome del pacchetto per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="b4979-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="b4979-112">Path</span><span class="sxs-lookup"><span data-stu-id="b4979-112">Path</span></span>| <span data-ttu-id="b4979-113">Percorso in cui si trova il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="b4979-113">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="b4979-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="b4979-114">ProductId</span></span>| <span data-ttu-id="b4979-115">Indica l'ID prodotto che identifica in modo univoco il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="b4979-115">Indicates the product ID that uniquely identifies the package.</span></span>|
| <span data-ttu-id="b4979-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="b4979-116">Arguments</span></span>| <span data-ttu-id="b4979-117">Elenca una stringa di argomenti che verrà passata al pacchetto esattamente nel modo specificato.</span><span class="sxs-lookup"><span data-stu-id="b4979-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="b4979-118">Credential</span><span class="sxs-lookup"><span data-stu-id="b4979-118">Credential</span></span>| <span data-ttu-id="b4979-119">Fornisce l'accesso al pacchetto in un'origine remota.</span><span class="sxs-lookup"><span data-stu-id="b4979-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="b4979-120">Questa proprietà non viene usata per installare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="b4979-120">This property is not used to install the package.</span></span> <span data-ttu-id="b4979-121">Il pacchetto viene sempre installato nel sistema locale.</span><span class="sxs-lookup"><span data-stu-id="b4979-121">The package is always installed on the local system.</span></span>|
| <span data-ttu-id="b4979-122">Ensure</span><span class="sxs-lookup"><span data-stu-id="b4979-122">Ensure</span></span>| <span data-ttu-id="b4979-123">Indica se il pacchetto è installato.</span><span class="sxs-lookup"><span data-stu-id="b4979-123">Indicates if the package is installed.</span></span> <span data-ttu-id="b4979-124">Impostare questa proprietà su "Absent" per specificare che il pacchetto non è installato (o disinstallare il pacchetto se è installato).</span><span class="sxs-lookup"><span data-stu-id="b4979-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="b4979-125">Impostarla su "Present" (valore predefinito) per specificare che il pacchetto è installato.</span><span class="sxs-lookup"><span data-stu-id="b4979-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="b4979-126">LogPath</span><span class="sxs-lookup"><span data-stu-id="b4979-126">LogPath</span></span>| <span data-ttu-id="b4979-127">Indica il percorso completo in cui il provider deve salvare un file di log per installare o disinstallare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="b4979-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="b4979-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b4979-128">DependsOn</span></span> | <span data-ttu-id="b4979-129">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="b4979-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b4979-130">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b4979-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="b4979-131">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="b4979-131">ReturnCode</span></span>| <span data-ttu-id="b4979-132">Indica il codice restituito previsto.</span><span class="sxs-lookup"><span data-stu-id="b4979-132">Indicates the expected return code.</span></span> <span data-ttu-id="b4979-133">Se l'effettivo codice restituito non corrisponde al valore previsto specificato qui, la configurazione restituirà un errore.</span><span class="sxs-lookup"><span data-stu-id="b4979-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|

## <a name="example"></a><span data-ttu-id="b4979-134">Esempio</span><span class="sxs-lookup"><span data-stu-id="b4979-134">Example</span></span>

<span data-ttu-id="b4979-135">Questo esempio esegue il programma di installazione MSI che si trova nel percorso specificato e che ha l'ID prodotto indicato.</span><span class="sxs-lookup"><span data-stu-id="b4979-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

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