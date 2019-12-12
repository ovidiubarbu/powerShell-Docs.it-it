---
ms.date: 06/12/2017
contributor: manikb
keywords: raccolta,powershell,cmdlet,psget
title: Risoluzione dei problemi relativi a cmdlet
ms.openlocfilehash: d87c680472c2588efbfe8b3c4d6f2dbee6883a0c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352118"
---
# <a name="troubleshooting-cmdlets"></a>Risoluzione dei problemi relativi a cmdlet

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Come risolvere il problema "AVVISO: Impossibile scaricare il pacchetto 'nome pacchetto'"

È stato segnalato che `Install-Module` o `Update-Module` talvolta causa errori in alcuni computer. In base alle ricerche effettuate, il problema ha probabilmente a che fare con la connessione di rete. Di recente è stato aggiornato il provider NuGet per assicurare il download affidabile dei pacchetti. È possibile usare le istruzioni riportate di seguito per installare la build più recente del provider NuGet e quindi installare o aggiornare il proprio modulo. Nell'esempio viene usato il modulo 'Azure'.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a>Endpoint di rete richiesti

I cmdlet di installazione e aggiornamento richiedono l'accesso a Internet per connettersi agli endpoint di rete usati da PowerShell Gallery. Assicurarsi che i criteri di accesso alla rete consentano di connettersi agli endpoint seguenti.

- oneget.org
- go.microsoft.com
- az818661.vo.msecnd.net
- [www.powershellgallery.com](www.powershellgallery.com)
- devopsgallerystorage.blob.core.windows.net
