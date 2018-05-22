---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 9ca12ad3f0729a2e9595d7ca5ccf9041e47658a3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
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
