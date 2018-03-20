---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: raccolta,powershell,cmdlet,psgallery, psget
title: PowerShell Gallery
ms.openlocfilehash: 7389ce8286c515b0bfc25f32634a482b060cb74c
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="the-powershell-gallery"></a>PowerShell Gallery

PowerShell Gallery è il repository centrale per i contenuti PowerShell. In PowerShell Gallery è possibile trovare nuovi comandi di PowerShell o risorse DSC (Desired State Configuration).

## <a name="powershellget-overview"></a>Panoramica di PowerShellGet

Il modulo PowerShellGet contiene i cmdlet per l'individuazione, l'installazione, l'aggiornamento e la pubblicazione di elementi PowerShell quali moduli, risorse DSC, capacità del ruolo e script da [PowerShell Gallery](https://www.PowerShellGallery.com) e altri repository privati.

## <a name="getting-started-with-the-gallery"></a>Introduzione a PowerShell Gallery

L'installazione degli elementi di PowerShell Gallery richiede la versione più recente del modulo PowerShellGet, disponibile in Windows 10, in Windows Management Framework (WMF) 5.0 o nel programma di installazione basato su MSI (per PowerShell 3 e 4).

- [**Ottenere Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),
- [**Ottenere WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175) o
- [**Ottenere il programma di installazione MSI**](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

Con la versione più recente del modulo [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), è possibile:

-   Cercare elementi in PowerShell Gallery con [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) e [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)
-   Salvare elementi nel sistema da PowerShell Gallery con [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) e [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)
-   Installare elementi da PowerShell Gallery con [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) e [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)
-   Caricare elementi in PowerShell Gallery con [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) e [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)
-   Aggiungere il proprio repository personalizzato con [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)

Per altre informazioni su come usare i comandi PowerShellGet con PowerShell Gallery, consultare la pagina [Introduzione](psgallery/psgallery_gettingstarted.md). È inoltre possibile eseguire *Update-Help -Module PowerShellGet* per installare la Guida locale per tali comandi.

## <a name="supported-operating-systems"></a>Sistemi operativi supportati

Il modulo **PowerShellGet** richiede **PowerShell 3.0 o versione successiva**.

Di conseguenza, **PowerShellGet** richiede uno dei sistemi operativi seguenti:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** richiede inoltre .NET Framework 4.5 o versione successiva. È possibile installare .NET Framework 4.5 o versione successiva da [qui](https://msdn.microsoft.com/library/5a4x27ek.aspx).


## <a name="got-a-question-have-feedback"></a>Domande? Commenti e suggerimenti?

Altre informazioni su PowerShell Gallery e PowerShellGet sono disponibili nella pagina [Introduzione](psgallery/psgallery_gettingstarted.md). Fornire commenti e suggerimenti e segnalare problemi usando [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).

