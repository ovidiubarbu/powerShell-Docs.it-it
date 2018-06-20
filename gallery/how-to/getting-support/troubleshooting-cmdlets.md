---
ms.date: 06/12/2017
contributor: manikb
keywords: raccolta,powershell,cmdlet,psget
title: Risoluzione dei problemi relativi a cmdlet
ms.openlocfilehash: e8890cb6bbe661b8524d83cabf91483acbde8095
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219828"
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