---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_cmdlets_troubleshooting
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 740c72620e1a5a114716f924f859c57cad125614

---

## Come risolvere il problema segnalato da un messaggio simile a: "AVVISO: Impossibile scaricare il pacchetto 'nome pacchetto'"




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




<!--HONumber=Oct16_HO2-->


