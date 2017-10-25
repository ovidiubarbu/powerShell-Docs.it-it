---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 7ad4a00f7beba0de70696d88cd5448c7c638c50c
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2017
---
# <a name="archive-cmdlets"></a><span data-ttu-id="333ff-102">Cmdlet Archive</span><span class="sxs-lookup"><span data-stu-id="333ff-102">Archive cmdlets</span></span>

<span data-ttu-id="333ff-103">Due nuovi cmdlet, **Compress-Archive** ed **Expand-Archive**, consentono di comprimere ed espandere i file ZIP.</span><span class="sxs-lookup"><span data-stu-id="333ff-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="333ff-104">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="333ff-104">Compress-Archive</span></span>
<span data-ttu-id="333ff-105">Il cmdlet **Compress-Archive** crea un nuovo file di archivio dai file specificati.</span><span class="sxs-lookup"><span data-stu-id="333ff-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="333ff-106">Un file di archivio consente di includere più file in un pacchetto e facoltativamente di comprimerli in un singolo file per facilitarne la gestione e l'archiviazione.</span><span class="sxs-lookup"><span data-stu-id="333ff-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="333ff-107">Un file di archivio può essere compresso tramite un algoritmo di compressione specificato nel parametro **-CompressionLevel**.</span><span class="sxs-lookup"><span data-stu-id="333ff-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>] 
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="333ff-108">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="333ff-108">Expand-Archive</span></span>
<span data-ttu-id="333ff-109">Il cmdlet **Expand-Archive** estrae i file da un file di archivio specificato.</span><span class="sxs-lookup"><span data-stu-id="333ff-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="333ff-110">Un file di archivio consente di includere più file in un pacchetto e facoltativamente di comprimerli in un singolo file per facilitarne la gestione e l'archiviazione.</span><span class="sxs-lookup"><span data-stu-id="333ff-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```

