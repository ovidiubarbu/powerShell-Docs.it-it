---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Risorsa Archive DSC
ms.openlocfilehash: 035f7cc1b7f21f7a0df2d72db0ba83bc0688356c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="f5e70-103">Risorsa Archive DSC</span><span class="sxs-lookup"><span data-stu-id="f5e70-103">DSC Archive Resource</span></span>

> <span data-ttu-id="f5e70-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f5e70-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f5e70-105">La risorsa Archive in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per decomprimere file di archivio (ZIP) in un percorso specifico.</span><span class="sxs-lookup"><span data-stu-id="f5e70-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="f5e70-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f5e70-106">Syntax</span></span> 
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="f5e70-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="f5e70-107">Properties</span></span>

|  <span data-ttu-id="f5e70-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="f5e70-108">Property</span></span>  |  <span data-ttu-id="f5e70-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f5e70-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="f5e70-110">Destination</span><span class="sxs-lookup"><span data-stu-id="f5e70-110">Destination</span></span>| <span data-ttu-id="f5e70-111">Indica il percorso in cui si vuole specificare di estrarre il contenuto dell'archivio.</span><span class="sxs-lookup"><span data-stu-id="f5e70-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span>| 
| <span data-ttu-id="f5e70-112">Path</span><span class="sxs-lookup"><span data-stu-id="f5e70-112">Path</span></span>| <span data-ttu-id="f5e70-113">Specifica il percorso di origine del file di archivio.</span><span class="sxs-lookup"><span data-stu-id="f5e70-113">Specifies the source path of the archive file.</span></span>| 
| <span data-ttu-id="f5e70-114">__Checksum__</span><span class="sxs-lookup"><span data-stu-id="f5e70-114">__Checksum__</span></span>| <span data-ttu-id="f5e70-115">Definisce il tipo da usare per determinare se due file sono uguali.</span><span class="sxs-lookup"><span data-stu-id="f5e70-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="f5e70-116">Se la proprietà __Checksum__ non è specificata, per il confronto viene usato solo il nome del file o della directory.</span><span class="sxs-lookup"><span data-stu-id="f5e70-116">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="f5e70-117">I valori validi includono: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate e none (predefinito).</span><span class="sxs-lookup"><span data-stu-id="f5e70-117">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (default).</span></span> <span data-ttu-id="f5e70-118">Se si specifica __Checksum__ senza __Validate__, la configurazione non riesce.</span><span class="sxs-lookup"><span data-stu-id="f5e70-118">If you specify __Checksum__ without __Validate__, the configuration will fail.</span></span>| 
| <span data-ttu-id="f5e70-119">Ensure</span><span class="sxs-lookup"><span data-stu-id="f5e70-119">Ensure</span></span>| <span data-ttu-id="f5e70-120">Determina se verificare l'esistenza del contenuto dell'archivio in __Destination__.</span><span class="sxs-lookup"><span data-stu-id="f5e70-120">Determines whether to check if the content of the archive exists at the __Destination__.</span></span> <span data-ttu-id="f5e70-121">Impostare questa proprietà su __Present__ per specificare che il contenuto esiste.</span><span class="sxs-lookup"><span data-stu-id="f5e70-121">Set this property to __Present__ to ensure the contents exist.</span></span> <span data-ttu-id="f5e70-122">Impostarla su __Absent__ per specificare che il contenuto non esiste.</span><span class="sxs-lookup"><span data-stu-id="f5e70-122">Set it to __Absent__ to ensure they do not exist.</span></span> <span data-ttu-id="f5e70-123">Il valore predefinito è __Present__.</span><span class="sxs-lookup"><span data-stu-id="f5e70-123">The default value is __Present__.</span></span>| 
| <span data-ttu-id="f5e70-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f5e70-124">DependsOn</span></span> | <span data-ttu-id="f5e70-125">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="f5e70-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f5e70-126">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f5e70-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="f5e70-127">Validate</span><span class="sxs-lookup"><span data-stu-id="f5e70-127">Validate</span></span>| <span data-ttu-id="f5e70-128">Usa la proprietà Checksum per determinare se l'archivio corrisponde alla firma.</span><span class="sxs-lookup"><span data-stu-id="f5e70-128">Uses the Checksum property to determine if the archive matches the signature.</span></span> <span data-ttu-id="f5e70-129">Se si specifica Checksum senza Validate, la configurazione non riesce.</span><span class="sxs-lookup"><span data-stu-id="f5e70-129">If you specify Checksum without Validate, the configuration will fail.</span></span> <span data-ttu-id="f5e70-130">Se si specifica Validate senza Checksum, per impostazione predefinita viene usato un checksum SHA-256.</span><span class="sxs-lookup"><span data-stu-id="f5e70-130">If you specify Validate without Checksum, a SHA-256 checksum is used by default.</span></span>| 
| <span data-ttu-id="f5e70-131">Force</span><span class="sxs-lookup"><span data-stu-id="f5e70-131">Force</span></span>| <span data-ttu-id="f5e70-132">Determinate operazioni sui file, ad esempio quando si sovrascrive un file o si elimina una directory non vuota, generano un errore.</span><span class="sxs-lookup"><span data-stu-id="f5e70-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="f5e70-133">Usando la proprietà Force, tali errori vengono ignorati.</span><span class="sxs-lookup"><span data-stu-id="f5e70-133">Using the Force property overrides such errors.</span></span> <span data-ttu-id="f5e70-134">Il valore predefinito è False.</span><span class="sxs-lookup"><span data-stu-id="f5e70-134">The default value is False.</span></span>| 

## <a name="example"></a><span data-ttu-id="f5e70-135">Esempio</span><span class="sxs-lookup"><span data-stu-id="f5e70-135">Example</span></span>

<span data-ttu-id="f5e70-136">L'esempio seguente mostra come usare la risorsa Archive per specificare che il contenuto di un file di archivio denominato Test.zip esiste e viene estratto in una determinata destinazione.</span><span class="sxs-lookup"><span data-stu-id="f5e70-136">The following example shows how to use the Archive resource to ensure that the contents of an archive file called Test.zip exist and are extracted at a given destination.</span></span>

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
} 
```

