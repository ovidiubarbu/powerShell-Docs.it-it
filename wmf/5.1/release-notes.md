---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
title: Note sulla versione di WMF 5.1
ms.openlocfilehash: eb22267c1af28a9fcdd049c76d363fff687f6167
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Note sulla versione di Windows Management Framework (WMF) 5.1 #

WMF 5.1 include i componenti PowerShell, WMI, WinRM e Registrazione inventario software (SIL) rilasciati con Windows Server 2016.
WMF 5.1 può essere installato in Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e offre alcuni miglioramenti rispetto a WMF 5.0 RTM, tra cui:

- Nuovi cmdlet: utenti locali e gruppi; Get-ComputerInfo
- I miglioramenti apportati a PowerShellGet includono l'applicazione di moduli firmati e l'installazione di moduli JEA
- È stato aggiunto il supporto di PackageManagement per i contenitori, l'installazione di CBS, l'installazione basata su EXE e i pacchetti CAB
- Miglioramenti del debug per le classi DSC e PowerShell
- Miglioramenti relativi alla sicurezza, incluso quando si usano i cmdlet PowerShellGet e quando si applicano i moduli firmati da catalogo provenienti dal server di pull
- Risposte ad alcune richieste o problemi segnalati da utenti

**Note importanti:**

- **WMF 5.1 richiede .NET Framework 4.5.2** (o versione successiva). Se .NET 4.5.2 (o versione successiva) non è disponibile, WMF verrà installato correttamente, ma le funzionalità principali non verranno eseguite. Le istruzioni sono disponibili nell'argomento [Installare e configurare WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure).
- WMF 5.1 deve essere disinstallato prima dell'installazione WMF 5.1 RTM.
- È possibile installare WMF 5.1 direttamente su WMF 5.0 o WMF 4.0.
- __Non è necessario__ installare WMF 4.0 prima di installare WMF 5.1 in Windows 7 e Windows Server 2008 R2. Questo problema presente nella versione di WMF 5.1 (anteprima) è stato risolto.