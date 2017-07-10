---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: d23cfc2aaa680c247aaab91d8875c64c9d62187e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="archive-cmdlets" class="xliff"></a>
# Cmdlet Archive

Due nuovi cmdlet, **Compress-Archive** ed **Expand-Archive**, consentono di comprimere ed espandere i file ZIP.

<a id="compress-archive" class="xliff"></a>
## Compress-Archive
Il cmdlet **Compress-Archive** crea un nuovo file di archivio dai file specificati. Un file di archivio consente di includere più file in un pacchetto e facoltativamente di comprimerli in un singolo file per facilitarne la gestione e l'archiviazione. Un file di archivio può essere compresso tramite un algoritmo di compressione specificato nel parametro **-CompressionLevel**.
```PowerShell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>] 
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

<a id="expand-archive" class="xliff"></a>
## Expand-Archive
Il cmdlet **Expand-Archive** estrae i file da un file di archivio specificato. Un file di archivio consente di includere più file in un pacchetto e facoltativamente di comprimerli in un singolo file per facilitarne la gestione e l'archiviazione.
```PowerShell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```

