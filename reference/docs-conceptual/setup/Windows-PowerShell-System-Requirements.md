---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Requisiti di sistema di Windows PowerShell
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
ms.openlocfilehash: 8850cf26b0313dfb8898ccb66b4767d695860d4c
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320738"
---
# <a name="windows-powershell-system-requirements"></a>Requisiti di sistema di Windows PowerShell
Questo argomento elenca i requisiti di sistema per Windows PowerShell 3.0, Windows PowerShell 4.0, Windows PowerShell 5.0 e Windows PowerShell 5.1 e per le funzionalità speciali, ad esempio Windows PowerShell Integrated Scripting Environment (ISE), i comandi CIM e i flussi di lavoro.

Windows® 8.1 e Windows Server® 2012 R2 includono tutti i programmi necessari. Questo argomento è progettato per gli utenti delle versioni precedenti di Windows.

## <a name="operating-system-requirements"></a>Requisiti del sistema operativo
Windows PowerShell 5.1 può essere eseguito nelle versioni seguenti di Windows.

- Windows Server 2019, installato per impostazione predefinita

- Windows Server 2016, installato per impostazione predefinita

- Windows Server 2012 R2, installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) per eseguire Windows PowerShell 5.1

- Windows Server 2012, installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) per eseguire Windows PowerShell 5.0

- Windows Server 2008 R2 con Service Pack 1, installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) per eseguire Windows PowerShell 5.1

- Windows 10 versione 1607 e successive, installato per impostazione predefinita

- Windows Server 10 versioni 1507, 1511, installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) per eseguire Windows PowerShell 5.1

- Windows 8.1, installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) per eseguire Windows PowerShell 5.1

- Windows 7 con Service Pack 1, installare [Windows Management Framework 5.1](https://aka.ms/wmf5download) per eseguire Windows PowerShell 5.1

Windows PowerShell 5.0 (superato da Windows PowerShell 5.1) viene eseguito nelle versioni seguenti di Windows.

- Windows Server 2019, versione successiva installata per impostazione predefinita

- Windows Server 2016, versione successiva installata per impostazione predefinita

- Windows Server 2012 R2, installare [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) per eseguire Windows PowerShell 5.0

- Windows Server 2012, installare [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) per eseguire Windows PowerShell 5.0

- Windows Server 2008 R2 con Service Pack 1, installare [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) per eseguire Windows PowerShell 5.0

- Windows 10 versione 1607 e versioni successive, versione successiva installata per impostazione predefinita

- Windows 10 versioni 1507, 1511, installato per impostazione predefinita

- Windows 8.1, installare [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) per eseguire Windows PowerShell 5.0

- Windows 7 con Service Pack 1, installare [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) per eseguire Windows PowerShell 5.0

Windows PowerShell 4.0 può essere eseguito nelle versioni seguenti di Windows.

- Windows 8.1, installato per impostazione predefinita

- Windows Server 2012 R2, installato per impostazione predefinita

- Windows® 7 con Service Pack 1, installare [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) per eseguire Windows PowerShell 4.0

- Windows Server® 2008 R2 con Service Pack 1, installare [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) per eseguire Windows PowerShell 4.0

Windows PowerShell 3.0 può essere eseguito nelle versioni seguenti di Windows.

- Windows 8, installato per impostazione predefinita

- Windows Server 2012, installato per impostazione predefinita

- Windows® 7 con Service Pack 1, installare [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) per eseguire Windows PowerShell 3.0

- Windows Server® 2008 R2 con Service Pack 1, installare [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) per eseguire Windows PowerShell 3.0

- Windows Server 2008 con Service Pack 2, installare [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) per eseguire Windows PowerShell 3.0

## <a name="microsoft-net-framework-requirements"></a>Requisiti di Microsoft .NET Framework
Windows PowerShell 5.1 richiede l'installazione completa di Microsoft .NET Framework 4.5. Windows Server 8.1 e Windows Server 2012 R2 includono Microsoft .NET Framework 4.5 per impostazione predefinita.

Windows PowerShell 5.0 richiede l'installazione completa di Microsoft .NET Framework 4.5. Windows Server 8.1 e Windows Server 2012 R2 includono Microsoft .NET Framework 4.5 per impostazione predefinita.

Windows PowerShell 4.0 richiede l'installazione completa di Microsoft .NET Framework 4.5. Windows Server 8.1 e Windows Server 2012 R2 includono Microsoft .NET Framework 4.5 per impostazione predefinita.

Windows PowerShell 3.0 richiede l'installazione completa di Microsoft .NET Framework 4. Windows 8 e Windows Server 2012 includono Microsoft .NET Framework 4.5 per impostazione predefinita, che soddisfa questo requisito.

Per installare Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe), vedere [Microsoft .NET Framework 4.5](https://go.microsoft.com/fwlink/?LinkID=242919) nel Download Center di Microsoft.

Per installare la versione completa di Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe), vedere [Microsoft .NET Framework 4 (Web Installer)](https://go.microsoft.com/fwlink/?LinkID=212931) nel Download Center di Microsoft.

## <a name="windows-management-framework-40"></a>Windows Management Framework 4.0
Windows PowerShell 5.0 richiede la preinstallazione di Windows Management Framework 4.0 in Windows Server 2008 R2 SP1 e Windows 7 SP1.

## <a name="ws-management-30"></a>WS-Management 3.0
Windows PowerShell 3.0 e Windows PowerShell 4.0 richiedono WS-Management 3.0, che supporta il servizio WinRM e il protocollo WS-Management. Questo programma è incluso in Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 e Windows Management Framework 3.0.

## <a name="windows-management-instrumentation-30"></a>Strumentazione gestione Windows 3.0
Windows PowerShell 3.0 e Windows PowerShell 4.0 richiedono Strumentazione gestione Windows 3.0 (WMI). Questo programma è incluso in Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 e Windows Management Framework 3.0. Se il programma non è installato nel computer, le funzionalità che richiedono WMI, ad esempio i comandi CIM, non vengono eseguite.

## <a name="common-language-runtime-40"></a>Common Language Runtime 4.0
Windows PowerShell 3.0, Windows PowerShell 4.0 e Windows PowerShell 5.0 vengono compilati in base a Common Language Runtime (CLR) 4.0.

## <a name="graphical-user-interface-requirements"></a>Requisiti dell'interfaccia utente grafica
Windows PowerShell è un'applicazione basata su console per cui non è necessaria un'interfaccia utente grafica. Di conseguenza, è particolarmente utile per i computer senza schermo o monitor oppure senza interfaccia utente, come le opzioni di installazione dei componenti di base del server di Windows Server 2012 R2 o Windows Server 2012.

Per alcuni elementi come i seguenti, tuttavia, è necessaria un'interfaccia utente grafica. Per informazioni dettagliate, vedere l'argomento della Guida per ogni elemento.

- Windows PowerShell Integrated Scripting Environment (ISE)

- Cmdlet

    1.  [Out-GridView](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview)

    2.  [Show-Command](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Show-Command)

    3.  [Show-ControlPanelItem](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)

    4.  [Show-EventLog](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)

- Parametri

    1.  Parametro **ShowWindow** del cmdlet [Get-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Get-Help).

    2.  Parametro **ShowSecurityDescriptorUi** dei cmdlet [Register-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) e [Set-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration).

## <a name="windows-powershell-engine-requirements"></a>Requisiti del motore di Windows PowerShell
Windows PowerShell 4.0 è progettato per essere compatibile con Windows PowerShell 3.0 e Windows PowerShell 2.0. I cmdlet, i provider, gli snap-in, i moduli e gli script scritti per Windows PowerShell 2.0 e Windows PowerShell 3.0 possono essere eseguiti senza modifiche in Windows PowerShell 4.0.

Tuttavia, a causa di una modifica nei criteri di attivazione di runtime in Microsoft .NET Framework 4, i programmi host di Windows PowerShell scritti per Windows PowerShell 2.0 e compilati con Common Language Runtime (CLR) 2.0 non possono essere eseguiti senza modifiche in Windows PowerShell 3.0, compilato con CLR 4.0.

Il motore di Windows PowerShell 2.0 richiede almeno Microsoft .NET Framework 2.0.50727. È possibile soddisfare questo requisito con Microsoft .NET Framework 3.5 Service Pack 1. Questo requisito non viene soddisfatto da Microsoft .NET Framework 4 e versioni successive di Microsoft .NET Framework.

Per informazioni sull'aggiunta o l'installazione del motore di Windows PowerShell 2.0 e l'aggiunta o l'installazione delle versioni richieste di Microsoft .NET Framework, vedere [Installazione del motore di Windows PowerShell 2.0](Installing-the-Windows-PowerShell-2.0-Engine.md). Per informazioni sull'avvio del motore di Windows PowerShell 2.0, vedere [Avvio del motore di Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="windows-preinstallation-environment"></a>Ambiente preinstallazione di Windows
Windows PowerShell 2.0, Windows PowerShell 3.0 e Windows PowerShell 4.0 eseguiti in Ambiente preinstallazione di Windows (Windows PE). I cmdlet seguenti non sono tuttavia supportati:

- [Cmdlet di BITS (Servizio trasferimento intelligente in background)](https://go.microsoft.com/fwlink/?LinkId=257514)

- [Get-EventLog](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)

- [Get-WinEvent](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)

- [Save-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Save-Help)

- [Update-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Update-Help)

Il servizio **WinRm** non è presente in Windows PE.

## <a name="see-also"></a>Vedere anche
- [Guida introduttiva a Windows PowerShell](../getting-started/Getting-Started-with-Windows-PowerShell.md)
- [Installazione di Windows PowerShell](Installing-Windows-PowerShell.md)
- [Avvio di Windows PowerShell](Starting-Windows-PowerShell.md)
