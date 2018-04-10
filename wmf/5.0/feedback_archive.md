---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 0c450d765531c18c0b73c5c64262e9895f92068a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="archive-cmdlets"></a>Cmdlet Archive

Due nuovi cmdlet, **Compress-Archive** ed **Expand-Archive**, consentono di comprimere ed espandere i file ZIP.

## <a name="compress-archive"></a>Compress-Archive
Il cmdlet **Compress-Archive** crea un nuovo file di archivio dai file specificati. Un file di archivio consente di includere più file in un pacchetto e facoltativamente di comprimerli in un singolo file per facilitarne la gestione e l'archiviazione. Un file di archivio può essere compresso tramite un algoritmo di compressione specificato nel parametro **-CompressionLevel**.
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a>Expand-Archive
Il cmdlet **Expand-Archive** estrae i file da un file di archivio specificato. Un file di archivio consente di includere più file in un pacchetto e facoltativamente di comprimerli in un singolo file per facilitarne la gestione e l'archiviazione.
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```