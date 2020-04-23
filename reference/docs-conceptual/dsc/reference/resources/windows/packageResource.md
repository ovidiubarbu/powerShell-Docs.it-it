---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Package DSC
ms.openlocfilehash: efac07b4b051564cadd5aa1542a6afda6cd453ad
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953148"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="18f84-103">Risorsa Package DSC</span><span class="sxs-lookup"><span data-stu-id="18f84-103">DSC Package Resource</span></span>

> <span data-ttu-id="18f84-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="18f84-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="18f84-105">La risorsa **Package** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per installare o disinstallare pacchetti, ad esempio i pacchetti di Windows Installer e setup.exe, nei nodi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="18f84-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="18f84-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="18f84-106">Syntax</span></span>

```Syntax
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ ReturnCode = [UInt32[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="18f84-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="18f84-107">Properties</span></span>

|<span data-ttu-id="18f84-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="18f84-108">Property</span></span> |<span data-ttu-id="18f84-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="18f84-109">Description</span></span> |
|---|---|
|<span data-ttu-id="18f84-110">Nome</span><span class="sxs-lookup"><span data-stu-id="18f84-110">Name</span></span> |<span data-ttu-id="18f84-111">Indica il nome del pacchetto per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="18f84-111">Indicates the name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="18f84-112">Path</span><span class="sxs-lookup"><span data-stu-id="18f84-112">Path</span></span> |<span data-ttu-id="18f84-113">Percorso in cui si trova il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="18f84-113">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="18f84-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="18f84-114">ProductId</span></span> |<span data-ttu-id="18f84-115">Indica l'ID prodotto che identifica in modo univoco il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="18f84-115">Indicates the product ID that uniquely identifies the package.</span></span> |
|<span data-ttu-id="18f84-116">Argomenti</span><span class="sxs-lookup"><span data-stu-id="18f84-116">Arguments</span></span> |<span data-ttu-id="18f84-117">Elenca una stringa di argomenti che verrà passata al pacchetto esattamente nel modo specificato.</span><span class="sxs-lookup"><span data-stu-id="18f84-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="18f84-118">Credenziale</span><span class="sxs-lookup"><span data-stu-id="18f84-118">Credential</span></span> |<span data-ttu-id="18f84-119">Fornisce l'accesso al pacchetto in un'origine remota.</span><span class="sxs-lookup"><span data-stu-id="18f84-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="18f84-120">Questa proprietà non viene usata per installare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="18f84-120">This property is not used to install the package.</span></span> <span data-ttu-id="18f84-121">Il pacchetto viene sempre installato nel sistema locale.</span><span class="sxs-lookup"><span data-stu-id="18f84-121">The package is always installed on the local system.</span></span> |
|<span data-ttu-id="18f84-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="18f84-122">LogPath</span></span> |<span data-ttu-id="18f84-123">Indica il percorso completo in cui il provider deve salvare un file di log per installare o disinstallare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="18f84-123">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |
|<span data-ttu-id="18f84-124">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="18f84-124">ReturnCode</span></span> |<span data-ttu-id="18f84-125">Indica il codice restituito previsto.</span><span class="sxs-lookup"><span data-stu-id="18f84-125">Indicates the expected return code.</span></span> <span data-ttu-id="18f84-126">Se l'effettivo codice restituito non corrisponde al valore previsto specificato qui, la configurazione restituirà un errore.</span><span class="sxs-lookup"><span data-stu-id="18f84-126">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="18f84-127">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="18f84-127">Common properties</span></span>

|<span data-ttu-id="18f84-128">Proprietà</span><span class="sxs-lookup"><span data-stu-id="18f84-128">Property</span></span> |<span data-ttu-id="18f84-129">Descrizione</span><span class="sxs-lookup"><span data-stu-id="18f84-129">Description</span></span> |
|---|---|
|<span data-ttu-id="18f84-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="18f84-130">DependsOn</span></span> |<span data-ttu-id="18f84-131">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="18f84-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="18f84-132">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="18f84-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="18f84-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="18f84-133">Ensure</span></span> |<span data-ttu-id="18f84-134">Indica se il pacchetto è installato.</span><span class="sxs-lookup"><span data-stu-id="18f84-134">Indicates if the package is installed.</span></span> <span data-ttu-id="18f84-135">Impostare questa proprietà su **Absent** per assicurarsi che il pacchetto non sia installato (o disinstallare il pacchetto se è installato).</span><span class="sxs-lookup"><span data-stu-id="18f84-135">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="18f84-136">Impostarla su **Present** per assicurarsi che il pacchetto sia installato.</span><span class="sxs-lookup"><span data-stu-id="18f84-136">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="18f84-137">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="18f84-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="18f84-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="18f84-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="18f84-139">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="18f84-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="18f84-140">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="18f84-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="18f84-141">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="18f84-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="18f84-142">Esempio</span><span class="sxs-lookup"><span data-stu-id="18f84-142">Example</span></span>

<span data-ttu-id="18f84-143">Questo esempio esegue il programma di installazione MSI che si trova nel percorso specificato e che ha l'ID prodotto indicato.</span><span class="sxs-lookup"><span data-stu-id="18f84-143">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

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