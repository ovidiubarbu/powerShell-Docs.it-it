---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: Risoluzione dei problemi relativi a cmdlet
ms.openlocfilehash: 6295a5b99aa19db933569638d84e490ad81eedc7
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="troubleshooting-cmdlets"></a>Risoluzione dei problemi relativi a cmdlet

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Come risolvere il problema segnalato da un messaggio simile a: "AVVISO: Impossibile scaricare il pacchetto 'nome pacchetto'"

È stato segnalato che il cmdlet Install-Module o Update-Module a volte genera un errore in alcuni computer.
In base alle ricerche effettuate, il problema ha probabilmente a che fare con la connessione di rete.
Di recente è stato aggiornato il provider NuGet per assicurare il download affidabile dei pacchetti.
È possibile usare le istruzioni riportate di seguito per installare la build più recente del provider NuGet e quindi installare o aggiornare il proprio modulo.
Nell'esempio viene usato il modulo 'Azure'.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```