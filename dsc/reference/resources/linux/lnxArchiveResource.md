---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxArchive DSC per Linux
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078045"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="fb1f8-103">Risorsa nxArchive DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="fb1f8-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="fb1f8-104">La risorsa **nxArchive** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per decomprimere file di archivio (TAR) in un percorso specifico in un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="fb1f8-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="fb1f8-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="fb1f8-105">Syntax</span></span>

```
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

## <a name="properties"></a><span data-ttu-id="fb1f8-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="fb1f8-106">Properties</span></span>

|  <span data-ttu-id="fb1f8-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="fb1f8-107">Property</span></span> |  <span data-ttu-id="fb1f8-108">Description</span><span class="sxs-lookup"><span data-stu-id="fb1f8-108">Description</span></span> |
|---|---|
| <span data-ttu-id="fb1f8-109">SourcePath</span><span class="sxs-lookup"><span data-stu-id="fb1f8-109">SourcePath</span></span>| <span data-ttu-id="fb1f8-110">Specifica il percorso di origine del file di archivio.</span><span class="sxs-lookup"><span data-stu-id="fb1f8-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="fb1f8-111">Può essere un file con estensione tar, zip o tar.gz.</span><span class="sxs-lookup"><span data-stu-id="fb1f8-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
| <span data-ttu-id="fb1f8-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="fb1f8-112">DestinationPath</span></span>| <span data-ttu-id="fb1f8-113">Indica il percorso in cui si vuole specificare di estrarre il contenuto dell'archivio.</span><span class="sxs-lookup"><span data-stu-id="fb1f8-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="fb1f8-114">Checksum</span><span class="sxs-lookup"><span data-stu-id="fb1f8-114">Checksum</span></span>| <span data-ttu-id="fb1f8-115">Definisce il tipo da usare per determinare se l'archivio di origine è stato aggiornato.</span><span class="sxs-lookup"><span data-stu-id="fb1f8-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="fb1f8-116">I valori sono: "ctime", "mtime" e "md5".</span><span class="sxs-lookup"><span data-stu-id="fb1f8-116">Values are: "ctime", "mtime", or "md5".</span></span> <span data-ttu-id="fb1f8-117">Il valore predefinito è "md5".</span><span class="sxs-lookup"><span data-stu-id="fb1f8-117">The default value is "md5".</span></span>|
| <span data-ttu-id="fb1f8-118">Force</span><span class="sxs-lookup"><span data-stu-id="fb1f8-118">Force</span></span>| <span data-ttu-id="fb1f8-119">Determinate operazioni sui file, ad esempio quando si sovrascrive un file o si elimina una directory non vuota, generano un errore.</span><span class="sxs-lookup"><span data-stu-id="fb1f8-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="fb1f8-120">Usando la proprietà **Force**, tali errori vengono ignorati.</span><span class="sxs-lookup"><span data-stu-id="fb1f8-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="fb1f8-121">Il valore predefinito è **$false**.</span><span class="sxs-lookup"><span data-stu-id="fb1f8-121">The default value is **$false**.</span></span>|
| <span data-ttu-id="fb1f8-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fb1f8-122">DependsOn</span></span> | <span data-ttu-id="fb1f8-123">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="fb1f8-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fb1f8-124">Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="fb1f8-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="fb1f8-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="fb1f8-125">Ensure</span></span>| <span data-ttu-id="fb1f8-126">Determina se verificare l'esistenza del contenuto dell'archivio in **Destination**.</span><span class="sxs-lookup"><span data-stu-id="fb1f8-126">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="fb1f8-127">Impostare questa proprietà su "Present" per specificare che il contenuto esiste.</span><span class="sxs-lookup"><span data-stu-id="fb1f8-127">Set this property to "Present" to ensure the contents exist.</span></span> <span data-ttu-id="fb1f8-128">Impostarla su "Absent" per specificare che il contenuto non esiste.</span><span class="sxs-lookup"><span data-stu-id="fb1f8-128">Set it to "Absent" to ensure they do not exist.</span></span> <span data-ttu-id="fb1f8-129">Il valore predefinito è "Present".</span><span class="sxs-lookup"><span data-stu-id="fb1f8-129">The default value is "Present".</span></span>|

## <a name="example"></a><span data-ttu-id="fb1f8-130">Esempio</span><span class="sxs-lookup"><span data-stu-id="fb1f8-130">Example</span></span>

<span data-ttu-id="fb1f8-131">L'esempio seguente mostra come usare la risorsa **nxArchive** per specificare che il contenuto di un file di archivio denominato `website.tar` esiste e viene estratto in una determinata destinazione.</span><span class="sxs-lookup"><span data-stu-id="fb1f8-131">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

```
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```