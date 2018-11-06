---
ms.date: 06/12/2017
contributor: manikb
keywords: raccolta,powershell,cmdlet,psget
title: Risoluzione dei problemi relativi a cmdlet
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002463"
---
# <a name="troubleshooting-cmdlets"></a>Risoluzione dei problemi relativi a cmdlet

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Come risolvere il problema segnalato da un messaggio di tipo "AVVISO: Impossibile scaricare il pacchetto 'nome pacchetto'"

È stato segnalato che `Install-Module` o `Update-Module` talvolta causa errori in alcuni computer.
In base alle ricerche effettuate, il problema ha probabilmente a che fare con la connessione di rete.
Di recente è stato aggiornato il provider NuGet per assicurare il download affidabile dei pacchetti.
È possibile usare le istruzioni riportate di seguito per installare la build più recente del provider NuGet e quindi installare o aggiornare il proprio modulo.
Nell'esempio viene usato il modulo 'Azure'.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
