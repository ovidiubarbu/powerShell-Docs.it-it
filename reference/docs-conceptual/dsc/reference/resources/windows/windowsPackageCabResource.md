---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsPackageCab DSC
ms.openlocfilehash: ec465b2c3b1d180ba46ee24a61f2be1129148962
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954638"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="cbed4-103">Risorsa WindowsPackageCab DSC</span><span class="sxs-lookup"><span data-stu-id="cbed4-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="cbed4-104">Si applica a: Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="cbed4-104">Applies To: Windows PowerShell 5.1</span></span>

<span data-ttu-id="cbed4-105">La risorsa **WindowsPackageCab** in Windows PowerShell DSC (Desired State Configuration) offre un meccanismo per installare o disinstallare pacchetti CAB in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="cbed4-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="cbed4-106">È necessario che nel nodo di destinazione sia installato il modulo PowerShell Gestione e manutenzione immagini distribuzione.</span><span class="sxs-lookup"><span data-stu-id="cbed4-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="cbed4-107">Per informazioni, vedere [Usare Gestione e manutenzione immagini distribuzione in Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="cbed4-107">For information, see [Use DISM in Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>

## <a name="syntax"></a><span data-ttu-id="cbed4-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cbed4-108">Syntax</span></span>

```Syntax
{
    Name = [string]
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    Ensure = [string] { Absent | Present }
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="cbed4-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="cbed4-109">Properties</span></span>

|<span data-ttu-id="cbed4-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="cbed4-110">Property</span></span> |<span data-ttu-id="cbed4-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="cbed4-111">Description</span></span> |
|---|---|
|<span data-ttu-id="cbed4-112">Nome</span><span class="sxs-lookup"><span data-stu-id="cbed4-112">Name</span></span> |<span data-ttu-id="cbed4-113">Indica il nome del pacchetto per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="cbed4-113">Indicates the name of the package for you want to ensure a specific state.</span></span> |
|<span data-ttu-id="cbed4-114">SourcePath</span><span class="sxs-lookup"><span data-stu-id="cbed4-114">SourcePath</span></span> |<span data-ttu-id="cbed4-115">Percorso in cui si trova il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="cbed4-115">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="cbed4-116">LogPath</span><span class="sxs-lookup"><span data-stu-id="cbed4-116">LogPath</span></span> |<span data-ttu-id="cbed4-117">Indica il percorso completo in cui il provider deve salvare un file di log per installare o disinstallare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="cbed4-117">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="cbed4-118">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="cbed4-118">Common properties</span></span>

|<span data-ttu-id="cbed4-119">Proprietà</span><span class="sxs-lookup"><span data-stu-id="cbed4-119">Property</span></span> |<span data-ttu-id="cbed4-120">Descrizione</span><span class="sxs-lookup"><span data-stu-id="cbed4-120">Description</span></span> |
|---|---|
|<span data-ttu-id="cbed4-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="cbed4-121">DependsOn</span></span> |<span data-ttu-id="cbed4-122">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="cbed4-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="cbed4-123">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="cbed4-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="cbed4-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="cbed4-124">Ensure</span></span> |<span data-ttu-id="cbed4-125">Indica se il pacchetto è installato.</span><span class="sxs-lookup"><span data-stu-id="cbed4-125">Indicates if the package is installed.</span></span> <span data-ttu-id="cbed4-126">Impostare questa proprietà su **Absent** per assicurarsi che il pacchetto non sia installato (o disinstallare il pacchetto se è installato).</span><span class="sxs-lookup"><span data-stu-id="cbed4-126">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="cbed4-127">Impostarla su **Present** per assicurarsi che il pacchetto sia installato.</span><span class="sxs-lookup"><span data-stu-id="cbed4-127">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="cbed4-128">**Ensure** è una proprietà obbligatoria per la risorsa **WindowsPackageCab**.</span><span class="sxs-lookup"><span data-stu-id="cbed4-128">**Ensure** is a required property on the **WindowsPackageCab** resource.</span></span> |
|<span data-ttu-id="cbed4-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="cbed4-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="cbed4-130">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="cbed4-130">Sets the credential for running the entire resource as.</span></span> |

## <a name="example"></a><span data-ttu-id="cbed4-131">Esempio</span><span class="sxs-lookup"><span data-stu-id="cbed4-131">Example</span></span>

<span data-ttu-id="cbed4-132">La configurazione di esempio seguente accetta parametri di input e assicura che venga installato il file con estensione cab specificato dal parametro `$Name`.</span><span class="sxs-lookup"><span data-stu-id="cbed4-132">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```