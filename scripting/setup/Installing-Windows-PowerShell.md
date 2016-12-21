---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Installazione di Windows PowerShell
ms.technology: powershell
ms.assetid: 6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
ms.openlocfilehash: fd0336b66312293c434ae2c5ad5a7899c20777ff
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="installing-windows-powershell"></a>Installazione di Windows PowerShell
Windows® 8 e Windows Server® 2012 includono Windows PowerShell 3.0 e tutti i relativi prerequisiti. Il sistema include anche il motore di Windows PowerShell 2.0 per la compatibilità con le versioni precedenti dei programmi host che non possono usare Windows PowerShell 3.0.

Questo argomento descrive come installare Windows PowerShell 3.0 nei sistemi precedenti, nonché come installare e abilitare le funzionalità necessarie.

Questo argomento include le sezioni seguenti:

-   [Installazione di Windows PowerShell in Windows 8 e Windows Server 2012](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [Installazione di Windows PowerShell in Windows 7 e Windows Server 2008 R2](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [Installazione di Windows PowerShell in Windows Server 2008](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [Installazione di Windows PowerShell in Server Core](Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [Distribuzione di Accesso Web Windows PowerShell](https://technet.microsoft.com/en-us/library/639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [Installazione del motore di Windows PowerShell 2.0](Installing-the-Windows-PowerShell-2.0-Engine.md)

## <a name="a-namebkmkinstallingonwindows8andwindowsserver2012ainstalling-windows-powershell-on-windows-8-and-windows-server-2012"></a><a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Installazione di Windows PowerShell in Windows 8 e Windows Server 2012
Windows PowerShell 3.0 viene fornito già installato, configurato e pronto per l'uso. Windows PowerShell Integrated Scripting Environment (ISE) viene installato e abilitato. Per informazioni sull'avvio di Windows PowerShell, vedere [Avvio di Windows PowerShell in Windows 8](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) e [Avvio di Windows PowerShell in Windows Server 2012](https://technet.microsoft.com/library/hh831491.aspx#BKMK_powershell).

## <a name="a-namebkmkinstallingonwindows7andwindowsserver2008r2ainstalling-windows-powershell-on-windows-7-and-windows-server-2008-r2"></a><a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Installazione di Windows PowerShell in Windows 7 e Windows Server 2008 R2
Queste istruzioni spiegano come installare Windows PowerShell 3.0 nei computer che eseguono Windows 7 con Service Pack 1 e Windows Server 2008 R2 con Service Pack 1. Di seguito sono disponibili istruzioni di installazione separate per i computer con l'opzione di installazione Server Core di Windows Server 2008 R2.

#### <a name="getting-ready-to-install"></a>Preparativi per l'installazione

-   Prima di installare Windows Management Framework 3.0, disinstallare eventuali versioni precedenti.

#### <a name="to-install-windows-powershell-30"></a>Per installare Windows PowerShell 3.0

1.  Installare la versione completa di Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).

    Oppure installare Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).

2.  Installare Windows Management Framework 3.0 dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

Per informazioni sull'avvio di Windows PowerShell 3.0, vedere [Avvio di Windows PowerShell in versioni precedenti di Windows](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md).

## <a name="a-namebkmkinstallingonservercoreainstalling-windows-powershell-on-server-core"></a><a name="BKMK_InstallingOnServerCore"></a>Installazione di Windows PowerShell in Server Core
Queste istruzioni spiegano come installare Windows PowerShell 3.0 nei computer che eseguono l'opzione di installazione Server Core di Windows Server 2008 R2 con Service Pack 1.

I primi passaggi della procedura usano i comandi Gestione e manutenzione immagini distribuzione per installare Microsoft NET Framework 2.0 per Server Core e Windows PowerShell 2.0. Questi programmi sono prerequisiti di Windows Management Framework 3.0, che viene installato in un passaggio successivo.

#### <a name="getting-ready-to-install"></a>Preparativi per l'installazione

-   Prima di installare Windows Management Framework 3.0, disinstallare eventuali versioni precedenti.

#### <a name="to-install-windows-powershell-30"></a>Per installare Windows PowerShell 3.0

1.  Avviare Cmd.exe

2.  Eseguire i seguenti comandi Gestione e manutenzione immagini distribuzione. Questi comandi installano .NET Framework 2.0 e Windows PowerShell 2.0.

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  Eseguire l'installazione completa di Microsoft .NET Framework 4.0 per Server Core dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450).

4.  Installare Windows Management Framework 3.0 dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

## <a name="a-namebkmkinstallingonwindowsserver2008lhainstalling-windows-powershell-on-windows-server-2008"></a><a name="BKMK_InstallingOnWindowsServer2008LH"></a>Installazione di Windows PowerShell in Windows Server 2008
Queste istruzioni spiegano come installare Windows PowerShell 3.0 nei computer che eseguono Windows Server 2008 con Service Pack 2.

Nei sistemi Windows Server 2008, Windows Management Framework (Windows PowerShell 2.0, KB 968930) è un prerequisito per Windows Management Framework 3.0. La funzionalità di "protezione estesa per l'autenticazione" protegge il computer da attacchi di inoltro dell'autenticazione e consente di usare il parametro **UseSSL** durante la creazione delle sessioni remote. Per installare Windows PowerShell 3.0 e il motore di Windows PowerShell 2.0, usare la procedura seguente.

#### <a name="getting-ready-to-install"></a>Preparativi per l'installazione

-   Prima di installare Windows Management Framework 3.0, disinstallare eventuali versioni precedenti.

#### <a name="to-install-windows-powershell-30"></a>Per installare Windows PowerShell 3.0

1.  Installare Microsoft .NET Framework 3.5 con Service Pack 1 dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910).

2.  Installare Windows Management Framework (Windows PowerShell 2.0, KB 968930) dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035).

3.  Installare la versione completa di Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).

    Oppure installare Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).

4.  Installare la "protezione estesa per l'autenticazione" (KB 968389) da [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398).

5.  Installare Windows Management Framework 3.0 dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

## <a name="see-also"></a>Vedere anche
- [Requisiti di sistema di Windows PowerShell](Windows-PowerShell-System-Requirements.md)
- [Avvio di Windows PowerShell](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)

