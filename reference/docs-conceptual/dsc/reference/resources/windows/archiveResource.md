---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Archive DSC
ms.openlocfilehash: ddabe1a623783fe213b8059f47851184d5253fc5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954768"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="762de-103">Risorsa Archive DSC</span><span class="sxs-lookup"><span data-stu-id="762de-103">DSC Archive Resource</span></span>

> <span data-ttu-id="762de-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="762de-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="762de-105">La risorsa Archive in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per decomprimere file di archivio (ZIP) in un percorso specifico.</span><span class="sxs-lookup"><span data-stu-id="762de-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="762de-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="762de-106">Syntax</span></span>

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="762de-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="762de-107">Properties</span></span>

|<span data-ttu-id="762de-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="762de-108">Property</span></span> |<span data-ttu-id="762de-109">Description</span><span class="sxs-lookup"><span data-stu-id="762de-109">Description</span></span> |
|---|---|
|<span data-ttu-id="762de-110">Destination</span><span class="sxs-lookup"><span data-stu-id="762de-110">Destination</span></span> |<span data-ttu-id="762de-111">Indica il percorso in cui si vuole specificare di estrarre il contenuto dell'archivio.</span><span class="sxs-lookup"><span data-stu-id="762de-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="762de-112">Path</span><span class="sxs-lookup"><span data-stu-id="762de-112">Path</span></span> |<span data-ttu-id="762de-113">Specifica il percorso di origine del file di archivio.</span><span class="sxs-lookup"><span data-stu-id="762de-113">Specifies the source path of the archive file.</span></span> |
|<span data-ttu-id="762de-114">Checksum</span><span class="sxs-lookup"><span data-stu-id="762de-114">Checksum</span></span> |<span data-ttu-id="762de-115">Definisce il tipo da usare per determinare se due file sono uguali.</span><span class="sxs-lookup"><span data-stu-id="762de-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="762de-116">Se la proprietà **Checksum** non è specificata, per il confronto viene usato solo il nome del file o della directory.</span><span class="sxs-lookup"><span data-stu-id="762de-116">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="762de-117">I valori validi includono: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span><span class="sxs-lookup"><span data-stu-id="762de-117">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> <span data-ttu-id="762de-118">Se si specifica **Checksum** senza **Validate**, la configurazione non riesce.</span><span class="sxs-lookup"><span data-stu-id="762de-118">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> |
|<span data-ttu-id="762de-119">Force</span><span class="sxs-lookup"><span data-stu-id="762de-119">Force</span></span> |<span data-ttu-id="762de-120">Determinate operazioni sui file, ad esempio quando si sovrascrive un file o si elimina una directory non vuota, generano un errore.</span><span class="sxs-lookup"><span data-stu-id="762de-120">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="762de-121">Usando la proprietà **Force**, tali errori vengono ignorati.</span><span class="sxs-lookup"><span data-stu-id="762de-121">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="762de-122">Il valore predefinito è **False**.</span><span class="sxs-lookup"><span data-stu-id="762de-122">The default value is **False**.</span></span> |
|<span data-ttu-id="762de-123">Validate</span><span class="sxs-lookup"><span data-stu-id="762de-123">Validate</span></span>| <span data-ttu-id="762de-124">Usa la proprietà **Checksum** per determinare se l'archivio corrisponde alla firma.</span><span class="sxs-lookup"><span data-stu-id="762de-124">Uses the **Checksum** property to determine if the archive matches the signature.</span></span> <span data-ttu-id="762de-125">Se si specifica **Checksum** senza **Validate**, la configurazione non riesce.</span><span class="sxs-lookup"><span data-stu-id="762de-125">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> <span data-ttu-id="762de-126">Se si specifica **Validate** senza **Checksum**, per impostazione predefinita viene usato un _checksum_ **SHA-256**.</span><span class="sxs-lookup"><span data-stu-id="762de-126">If you specify **Validate** without **Checksum**, a _SHA-256_ **Checksum** is used by default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="762de-127">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="762de-127">Common properties</span></span>

|<span data-ttu-id="762de-128">Proprietà</span><span class="sxs-lookup"><span data-stu-id="762de-128">Property</span></span> |<span data-ttu-id="762de-129">Description</span><span class="sxs-lookup"><span data-stu-id="762de-129">Description</span></span> |
|---|---|
|<span data-ttu-id="762de-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="762de-130">DependsOn</span></span> |<span data-ttu-id="762de-131">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="762de-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="762de-132">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="762de-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="762de-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="762de-133">Ensure</span></span> |<span data-ttu-id="762de-134">Determina se verificare l'esistenza del contenuto dell'archivio in **Destination**.</span><span class="sxs-lookup"><span data-stu-id="762de-134">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="762de-135">Impostare questa proprietà su **Present** per specificare che il contenuto esiste.</span><span class="sxs-lookup"><span data-stu-id="762de-135">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="762de-136">Impostarla su **Absent** per specificare che il contenuto non esiste.</span><span class="sxs-lookup"><span data-stu-id="762de-136">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="762de-137">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="762de-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="762de-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="762de-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="762de-139">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="762de-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="762de-140">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="762de-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="762de-141">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="762de-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="762de-142">Esempio</span><span class="sxs-lookup"><span data-stu-id="762de-142">Example</span></span>

<span data-ttu-id="762de-143">L'esempio seguente mostra come usare la risorsa Archive per assicurarsi che il contenuto di un file di archivio denominato `Test.zip` esista e venga estratto in una destinazione specificata.</span><span class="sxs-lookup"><span data-stu-id="762de-143">The following example shows how to use the Archive resource to ensure that the contents of an archive file called `Test.zip` exist and are extracted at a given destination.</span></span>

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```