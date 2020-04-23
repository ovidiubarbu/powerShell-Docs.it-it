---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxArchive DSC per Linux
ms.openlocfilehash: 77b52ad68344ba791501baeb585a5001cc97a126
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953328"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="797e1-103">Risorsa nxArchive DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="797e1-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="797e1-104">La risorsa **nxArchive** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per decomprimere file di archivio (TAR) in un percorso specifico in un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="797e1-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="797e1-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="797e1-105">Syntax</span></span>

```Syntax
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="797e1-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="797e1-106">Properties</span></span>

|<span data-ttu-id="797e1-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="797e1-107">Property</span></span> |<span data-ttu-id="797e1-108">Descrizione</span><span class="sxs-lookup"><span data-stu-id="797e1-108">Description</span></span> |
|---|---|
|<span data-ttu-id="797e1-109">SourcePath</span><span class="sxs-lookup"><span data-stu-id="797e1-109">SourcePath</span></span> |<span data-ttu-id="797e1-110">Specifica il percorso di origine del file di archivio.</span><span class="sxs-lookup"><span data-stu-id="797e1-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="797e1-111">Può essere un file con estensione tar, zip o tar.gz.</span><span class="sxs-lookup"><span data-stu-id="797e1-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
|<span data-ttu-id="797e1-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="797e1-112">DestinationPath</span></span> |<span data-ttu-id="797e1-113">Indica il percorso in cui si vuole specificare di estrarre il contenuto dell'archivio.</span><span class="sxs-lookup"><span data-stu-id="797e1-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="797e1-114">Checksum</span><span class="sxs-lookup"><span data-stu-id="797e1-114">Checksum</span></span> |<span data-ttu-id="797e1-115">Definisce il tipo da usare per determinare se l'archivio di origine è stato aggiornato.</span><span class="sxs-lookup"><span data-stu-id="797e1-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="797e1-116">I valori sono: **ctime**, **mtime** o **md5**.</span><span class="sxs-lookup"><span data-stu-id="797e1-116">Values are: **ctime**, **mtime**, or **md5**.</span></span> <span data-ttu-id="797e1-117">Il valore predefinito è **md5**.</span><span class="sxs-lookup"><span data-stu-id="797e1-117">The default value is **md5**.</span></span> |
|<span data-ttu-id="797e1-118">Force</span><span class="sxs-lookup"><span data-stu-id="797e1-118">Force</span></span> |<span data-ttu-id="797e1-119">Determinate operazioni sui file, ad esempio quando si sovrascrive un file o si elimina una directory non vuota, generano un errore.</span><span class="sxs-lookup"><span data-stu-id="797e1-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="797e1-120">Usando la proprietà **Force**, tali errori vengono ignorati.</span><span class="sxs-lookup"><span data-stu-id="797e1-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="797e1-121">Il valore predefinito è `$false`.</span><span class="sxs-lookup"><span data-stu-id="797e1-121">The default value is `$false`.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="797e1-122">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="797e1-122">Common properties</span></span>

|<span data-ttu-id="797e1-123">Proprietà</span><span class="sxs-lookup"><span data-stu-id="797e1-123">Property</span></span> |<span data-ttu-id="797e1-124">Descrizione</span><span class="sxs-lookup"><span data-stu-id="797e1-124">Description</span></span> |
|---|---|
|<span data-ttu-id="797e1-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="797e1-125">DependsOn</span></span> |<span data-ttu-id="797e1-126">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="797e1-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="797e1-127">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="797e1-127">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="797e1-128">Ensure</span><span class="sxs-lookup"><span data-stu-id="797e1-128">Ensure</span></span> |<span data-ttu-id="797e1-129">Determina se verificare l'esistenza del contenuto dell'archivio in **Destination**.</span><span class="sxs-lookup"><span data-stu-id="797e1-129">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="797e1-130">Impostare questa proprietà su **Present** per specificare che il contenuto esiste.</span><span class="sxs-lookup"><span data-stu-id="797e1-130">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="797e1-131">Impostarla su **Absent** per specificare che il contenuto non esiste.</span><span class="sxs-lookup"><span data-stu-id="797e1-131">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="797e1-132">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="797e1-132">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="797e1-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="797e1-133">Example</span></span>

<span data-ttu-id="797e1-134">L'esempio seguente mostra come usare la risorsa **nxArchive** per specificare che il contenuto di un file di archivio denominato `website.tar` esiste e viene estratto in una determinata destinazione.</span><span class="sxs-lookup"><span data-stu-id="797e1-134">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

```powershell
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = "http://release.contoso.com/releases/website.tar"
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = "mtime"
}

nxArchive SyncWebDir
{
   SourcePath = "/usr/release/staging/website.tar"
   DestinationPath = "/usr/local/apache2/htdocs/"
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```