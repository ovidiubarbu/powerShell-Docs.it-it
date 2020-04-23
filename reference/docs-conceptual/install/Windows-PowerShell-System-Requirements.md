---
ms.date: 12/06/2019
keywords: powershell,cmdlet
title: Requisiti di sistema di Windows PowerShell
ms.openlocfilehash: 713b062916fec0c5c70ea9a7f95fea3570afb64a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "74953790"
---
# <a name="windows-powershell-system-requirements"></a>Requisiti di sistema di Windows PowerShell

Questo articolo elenca i requisiti di sistema per Windows PowerShell 3.0, Windows PowerShell 4.0, Windows PowerShell 5.0 e Windows PowerShell 5.1, nonché per funzionalità speciali, come Windows PowerShell ISE (Integrated Scripting Environment), i comandi CIM (Common Information Model) e i flussi di lavoro.

Windows® 8.1 e Windows Server® 2012 R2 includono tutti i programmi necessari. Questo articolo è progettato per gli utenti delle versioni precedenti di Windows.

## <a name="operating-system-requirements"></a>Requisiti del sistema operativo

### <a name="windows-powershell-51"></a>Windows PowerShell 5.1

Windows PowerShell 5.1 può essere eseguito nelle versioni seguenti di Windows. Per eseguire Windows PowerShell 5.1, installare Windows Management Framework 5.1. Per altre informazioni, vedere [Installare e configurare WMF 5.1](../wmf/setup/install-configure.md).

| Versione di Windows | Requisito del sistema |
| ----- | ----- |
| Windows Server 2019 | Installato per impostazione predefinita |
| Windows Server 2016 | Installato per impostazione predefinita |
| Windows Server 2012 R2 | Installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2012 | Installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2008 R2 con Service Pack 1 | Installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 10 versione 1607 e successive | Installato per impostazione predefinita |
| Windows 10 versione 1507, 1511 | Installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 8.1 | Installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 7 con Service Pack 1 | Installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) |

### <a name="windows-powershell-50"></a>Windows PowerShell 5.0

Windows PowerShell 5.0 può essere eseguito nelle versioni seguenti di Windows. Per eseguire Windows PowerShell 5.0, installare Windows Management Framework 5.1. Per altre informazioni, vedere [Installare e configurare WMF 5.1](../wmf/setup/install-configure.md). Windows Management Framework 5.1 sostituisce Windows Management Framework 5.0.

| Versione di Windows | Requisito del sistema |
| ----- | ----- |
| Windows Server 2019 | Versione successiva installata per impostazione predefinita |
| Windows Server 2016 | Versione successiva installata per impostazione predefinita |
| Windows Server 2012 R2 | Installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2012 | Installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2008 R2 con Service Pack 1 | Installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 10 versione 1607 e successive | Versione successiva installata per impostazione predefinita |
| Windows 10 versione 1507, 1511 | Installato per impostazione predefinita |
| Windows 8.1 | Installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 7 con Service Pack 1 | Installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) |

### <a name="windows-powershell-40"></a>Windows PowerShell 4.0

Windows PowerShell 4.0 può essere eseguito nelle versioni seguenti di Windows. Per eseguire Windows PowerShell 4.0, installare la versione specificata di Windows Management Framework per il sistema operativo in uso.

| Versione di Windows | Requisito del sistema |
| ----- | ----- |
| Windows 8.1 | Installato per impostazione predefinita |
| Windows Server 2012 R2 | Installato per impostazione predefinita |
| Windows® 7 con Service Pack 1 | Installare [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) |
| Windows Server® 2008 R2 con Service Pack 1 | Installare [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) |

### <a name="windows-powershell-30"></a>Windows PowerShell 3.0

Windows PowerShell 3.0 può essere eseguito nelle versioni seguenti di Windows. Per eseguire Windows PowerShell 3.0, installare la versione specificata di Windows Management Framework per il sistema operativo in uso.

| Versione di Windows | Requisito del sistema |
| ----- | ----- |
| Windows 8 | Installato per impostazione predefinita |
| Windows Server 2012 | Installato per impostazione predefinita |
| Windows® 7 con Service Pack 1 | Installare [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) |
| Windows Server® 2008 R2 con Service Pack 1 | Installare [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) |
| Windows Server 2008 con Service Pack 2 | Installare [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) |

## <a name="microsoft-net-framework-requirements"></a>Requisiti di Microsoft .NET Framework

La tabella seguente illustra i requisiti di .NET Framework per Windows PowerShell.

| Versione | Requisito .NET |
| ----- | ----- |
| Windows PowerShell 5.1 | Richiede l'installazione completa di Microsoft .NET Framework 4.5. Windows Server 8.1 e Windows Server 2012 R2 includono Microsoft .NET Framework 4.5 per impostazione predefinita. |
| Windows PowerShell 5.0 | Richiede l'installazione completa di Microsoft .NET Framework 4.5. Windows Server 8.1 e Windows Server 2012 R2 includono Microsoft .NET Framework 4.5 per impostazione predefinita. |
| Windows PowerShell 4.0 | Richiede l'installazione completa di Microsoft .NET Framework 4.5. Windows Server 8.1 e Windows Server 2012 R2 includono Microsoft .NET Framework 4.5 per impostazione predefinita. |
| Windows PowerShell 3.0 | Richiede l'installazione completa di Microsoft .NET Framework 4. Windows 8 e Windows Server 2012 includono Microsoft .NET Framework 4.5 per impostazione predefinita, che soddisfa questo requisito. |

Usare i collegamenti seguenti per scaricare Microsoft .NET Framework dall'area download Microsoft.

| Versione | Collegamento |
| ----- | ----- |
| .NET Framework 4.5 (`dotNetFx45_Full_setup.exe`) | [Microsoft .NET Framework 4.5](https://go.microsoft.com/fwlink/?LinkID=242919) |
| .NET Framework 4 (`dotNetFx40_Full_setup.exe`) | [Microsoft .NET Framework 4 (programma di installazione Web)](https://www.microsoft.com/en-us/download/details.aspx?id=17851) |

## <a name="windows-management-framework-40"></a>Windows Management Framework 4.0

Windows PowerShell 5.0 richiede la preinstallazione di Windows Management Framework 4.0 in Windows Server 2008 R2 SP1 e Windows 7 SP1.

## <a name="ws-management-30"></a>WS-Management 3.0

Windows PowerShell 3.0 e Windows PowerShell 4.0 richiedono WS-Management 3.0, che supporta il servizio WinRM e il protocollo WS-Management. Questo programma è incluso in Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 e Windows Management Framework 3.0.

## <a name="windows-management-instrumentation-30"></a>Strumentazione gestione Windows 3.0

Windows PowerShell 3.0 e Windows PowerShell 4.0 richiedono Strumentazione gestione Windows 3.0 (WMI). Questo programma è incluso in Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 e Windows Management Framework 3.0. Se il programma non è installato nel computer, le funzionalità che richiedono WMI, ad esempio i comandi CIM, non vengono eseguite.

## <a name="common-language-runtime-40"></a>Common Language Runtime 4.0

Windows PowerShell 3.0, Windows PowerShell 4.0 e Windows PowerShell 5.0 vengono compilati in base a Common Language Runtime (CLR) 4.0.

## <a name="graphical-user-interface-requirements"></a>Requisiti dell'interfaccia utente grafica

Windows PowerShell è un'applicazione basata su console per cui non è necessaria un'interfaccia utente grafica.
È particolarmente utile per i computer senza schermo o monitor oppure senza interfaccia utente, come le opzioni di installazione dei componenti di base del server di Windows Server 2012 R2 o Windows Server 2012.

Per alcuni elementi è necessaria un'interfaccia utente grafica. Per informazioni dettagliate, vedere l'articolo della Guida per ogni elemento.

- Windows PowerShell ISE (Integrated Scripting Environment). Per altre informazioni, vedere [Introduzione a Windows PowerShell ISE](/powershell/scripting/components/ise/introducing-the-windows-powershell-ise).
- Cmdlet
  - [Out-GridView](/powershell/module/microsoft.powershell.utility/out-gridview)
  - [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command)
  - [Show-ControlPanelItem](/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)
  - [Show-EventLog](/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)
- Parametri
  - Parametro **ShowWindow** del cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help).
  - Parametro **ShowSecurityDescriptorUi** dei cmdlet [Register-PSSessionConfiguration](/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) e [Set-PSSessionConfiguration](/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration).

## <a name="windows-powershell-engine-requirements"></a>Requisiti del motore di Windows PowerShell

Windows PowerShell 4.0 è progettato per essere compatibile con Windows PowerShell 3.0 e Windows PowerShell 2.0. I cmdlet, i provider, gli snap-in, i moduli e gli script scritti per Windows PowerShell 2.0 e Windows PowerShell 3.0 possono essere eseguiti senza modifiche in Windows PowerShell 4.0.

Tuttavia, a causa di una modifica nei criteri di attivazione di runtime in Microsoft .NET Framework 4, i programmi host di Windows PowerShell scritti per Windows PowerShell 2.0 e compilati con Common Language Runtime (CLR) 2.0 non possono essere eseguiti senza modifiche in Windows PowerShell 3.0, compilato con CLR 4.0.

Il requisito minimo del motore di Windows PowerShell 2.0 è Microsoft .NET Framework 2.0.50727. È possibile soddisfare questo requisito con Microsoft .NET Framework 3.5 Service Pack 1. Questo requisito non viene soddisfatto da Microsoft .NET Framework 4 e versioni successive di Microsoft .NET Framework.

Per informazioni sull'aggiunta o l'installazione del motore di Windows PowerShell 2.0 e l'aggiunta o l'installazione delle versioni richieste di Microsoft .NET Framework, vedere [Installazione del motore di Windows PowerShell 2.0](Installing-the-Windows-PowerShell-2.0-Engine.md). Per informazioni sull'avvio del motore di Windows PowerShell 2.0, vedere [Avvio del motore di Windows PowerShell 2.0](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="windows-preinstallation-environment"></a>Ambiente preinstallazione di Windows

Windows PowerShell 2.0, Windows PowerShell 3.0 e Windows PowerShell 4.0 eseguiti in Ambiente preinstallazione di Windows (Windows PE). I cmdlet seguenti non sono tuttavia supportati.

- Cmdlet di BITS (Servizio trasferimento intelligente in background). Per altre informazioni, vedere [BitsTransfer](/powershell/module/bitstransfer/?view=win10-ps).
- [Get-EventLog](/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)
- [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)
- [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help)
- [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)

Il servizio **WinRM** non è presente in Windows PE.

## <a name="see-also"></a>Vedere anche

[Introduzione a Windows PowerShell](../getting-started/Getting-Started-with-Windows-PowerShell.md)

[Installazione di Windows PowerShell](Installing-Windows-PowerShell.md)

[Avvio di Windows PowerShell](../getting-started/Starting-Windows-PowerShell.md)

[Windows Management Framework](../wmf/overview.md)
