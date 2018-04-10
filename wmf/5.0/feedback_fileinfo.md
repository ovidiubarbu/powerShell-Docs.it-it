---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 6356902193fc6ec651b2f7e53f8885cb59f17542
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="updates-to-fileinfo-object"></a>Aggiornamenti dell'oggetto FileInfo
Le informazioni sulla versione dei file possono essere fuorvianti, in particolare in seguito all'applicazione di patch ai file. In questa versione di WMF 5.0 sono state aggiunte le nuove proprietà di script **FileVersionRaw** e **ProductVersionRaw** per gli oggetti FileInfo. Ecco le proprietà come vengono visualizzate per powershell.exe (presupponendo che $pid è l'ID del processo di PowerShell):

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117