---
title: Note sulla versione di WMF 5.1 (anteprima)
ms.date: 2016-07-27
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 5eb9eae6257cdb57f4f778b5dddf5aa7ef9d10bb
ms.openlocfilehash: 12f2c084ab92134b733ee037c3d9fbd512af2e4c

---

# Note sulla versione di Windows Management Framework (WMF) 5.1 (anteprima) #

WMF 5.1 (anteprima) include i componenti PowerShell, WMI, WinRM, Software Inventory and Licensing (SIL) che vengono rilasciati con Windows Server 2016. WMF 5.1 può essere installato in Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e offre alcuni miglioramenti rispetto a WMF 5.0 RTM, tra cui:

- Nuovi cmdlet: utenti locali e gruppi; Get-ComputerInfo
- I miglioramenti apportati a PowerShellGet includono l'applicazione di moduli firmati e l'installazione di moduli JEA
- È stato aggiunto il supporto di PackageManagement per i contenitori, l'installazione di CBS, l'installazione basata su EXE e i pacchetti CAB
- Miglioramenti del debug per le classi DSC e PowerShell
- Miglioramenti relativi alla sicurezza, incluso quando si usano i cmdlet PowerShellGet e quando si applicano i moduli firmati da catalogo provenienti dal server di pull
- Risposte ad alcune richieste o problemi segnalati da utenti

**Note importanti:**

- **WMF 5.1 (anteprima) richiede Windows Management Framework 4.6**. Se .Net 4.6 non è installato, WMF verrà installato correttamente, ma le funzioni principali non verranno eseguite. Le istruzioni sono disponibili nell'argomento [Installare e configurare WMF 5.1 (anteprima)](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure). 
- In questa fase **WMF 5.1 (anteprima) non è supportato per distribuzioni di produzione**. L'obiettivo di questa anteprima è quello di fornire informazioni preliminari sul contenuto della versione e offrire l'opportunità di inviare commenti al team PowerShell.
- È possibile installare WMF 5.1 (anteprima) direttamente su WMF 5.0.
- È un problema noto che è necessario aver installato WMF 4.0 per procedere all'installazione di WMF 5.1 (anteprima) in Windows 7 e Windows Server 2008. Si prevede di rimuovere questo requisito prima della versione finale.
- Per l'installazione di future versioni di WMF 5.1, inclusa la versione RTM, è richiesta la disinstallazione di WMF 5.1 (anteprima).



<!--HONumber=Jul16_HO5-->


