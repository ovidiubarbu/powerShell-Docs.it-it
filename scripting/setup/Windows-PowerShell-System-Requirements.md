---
title: Requisiti di sistema di Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
---
# Requisiti di sistema di Windows PowerShell
Questo argomento elenca i requisiti di sistema per Windows PowerShell 3.0 e Windows PowerShell 4.0 e per le funzionalità speciali, ad esempio Windows PowerShell Integrated Scripting Environment (ISE), i comandi CIM e i flussi di lavoro.

Windows® 8.1 e Windows Server® 2012 R2 includono tutti i programmi necessari. Questo argomento è progettato per gli utenti delle versioni precedenti di Windows.

## Requisiti del sistema operativo
Windows PowerShell 4.0 può essere eseguito nelle versioni seguenti di Windows.

-   Windows 8.1, installato per impostazione predefinita

-   Windows Server 2012 R2, installato per impostazione predefinita

-   Windows® 7 con Service Pack 1, installare [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) per eseguire Windows PowerShell 4.0

-   Windows Server® 2008 R2 con Service Pack 1, installare [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) per eseguire Windows PowerShell 4.0

Windows PowerShell 3.0 può essere eseguito nelle versioni seguenti di Windows.

-   Windows 8, installato per impostazione predefinita

-   Windows Server 2012, installato per impostazione predefinita

-   Windows® 7 con Service Pack 1, installare [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) per eseguire Windows PowerShell 3.0

-   Windows Server® 2008 R2 con Service Pack 1, installare [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) per eseguire Windows PowerShell 3.0

-   Windows Server 2008 con Service Pack 2, installare [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) per eseguire Windows PowerShell 3.0

## Requisiti di Microsoft .NET Framework
Windows PowerShell 4.0 richiede l'installazione completa di Microsoft .NET Framework 4.5. Windows Server 8.1 e Windows Server 2012 R2 includono Microsoft .NET Framework 4.5 per impostazione predefinita.

Windows PowerShell 3.0 richiede l'installazione completa di Microsoft .NET Framework 4. Windows 8 e Windows Server 2012 includono Microsoft .NET Framework 4.5 per impostazione predefinita, che soddisfa questo requisito.

Per installare Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe), vedere [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919) nell'Area download Microsoft.

Per installare la versione completa di Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe), vedere [Microsoft .NET Framework 4 (Web Installer)](http://go.microsoft.com/fwlink/?LinkID=212931) nell'Area download Microsoft.

## WS-Management 3.0
Windows PowerShell 3.0 e Windows PowerShell 4.0 richiedono WS-Management 3.0, che supporta il servizio WinRM e il protocollo WS-Management. Questo programma è incluso in Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 e Windows Management Framework 3.0.

## Strumentazione gestione Windows 3.0
Windows PowerShell 3.0 e Windows PowerShell 4.0 richiedono Strumentazione gestione Windows 3.0 (WMI). Questo programma è incluso in Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 e Windows Management Framework 3.0. Se il programma non è installato nel computer, le funzionalità che richiedono WMI, ad esempio i comandi CIM, non vengono eseguite.

## Common Language Runtime 4.0
Windows PowerShell 3.0 e Windows PowerShell 4.0 vengono compilati in base a Common Language Runtime (CLR) 4.0.

## Requisiti dell'interfaccia utente grafica
Windows PowerShell è un'applicazione basata su console per cui non è necessaria un'interfaccia utente grafica. Di conseguenza, è particolarmente utile per i computer senza schermo o monitor oppure senza interfaccia utente, come le opzioni di installazione dei componenti di base del server di Windows Server 2012 R2 o Windows Server 2012.

Per alcuni elementi come i seguenti, tuttavia, è necessaria un'interfaccia utente grafica. Per informazioni dettagliate, vedere l'argomento della Guida per ogni elemento.

-   Windows PowerShell Integrated Scripting Environment (ISE)

-   Cmdlet

    1.  [Out-GridView](https://technet.microsoft.com/en-us/library/70915a86-d753-464e-8349-cba02316154c)

    2.  [Show-Command](https://technet.microsoft.com/en-us/library/65bba50b-91a8-49d5-80a2-a30fc684ba41)

    3.  [Show-ControlPanelItem](https://technet.microsoft.com/en-us/library/0685d42c-37cc-498f-acf6-0ecfeb0cb162)

    4.  [Show-EventLog](https://technet.microsoft.com/en-us/library/a3b0f5ad-0438-42c7-915b-d1b4793a431c)

-   Parametri

    1.  Parametro **ShowWindow** del cmdlet [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a).

    2.  Parametro **ShowSecurityDescriptorUi** dei cmdlet [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) e [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea).

## Requisiti del motore di Windows PowerShell
Windows PowerShell 4.0 è progettato per essere compatibile con Windows PowerShell 3.0 e Windows PowerShell 2.0. I cmdlet, i provider, gli snap-in, i moduli e gli script scritti per Windows PowerShell 2.0 possono essere eseguiti senza modifiche in Windows PowerShell 3.0 e Windows PowerShell 4.0.

Tuttavia, a causa di una modifica nei criteri di attivazione di runtime in Microsoft .NET Framework 4, i programmi host di Windows PowerShell scritti per Windows PowerShell 2.0 e compilati con Common Language Runtime (CLR) 2.0 non possono essere eseguiti senza modifiche in Windows PowerShell 3.0, compilato con CLR 4.0.

Il motore di Windows PowerShell 2.0 richiede almeno Microsoft .NET Framework 2.0.50727. È possibile soddisfare questo requisito con Microsoft .NET Framework 3.5 Service Pack 1. Questo requisito non viene soddisfatto da Microsoft .NET Framework 4 e versioni successive di Microsoft .NET Framework.

Per informazioni sull'aggiunta o l'installazione del motore di Windows PowerShell 2.0 e l'aggiunta o l'installazione delle versioni richieste di Microsoft .NET Framework, vedere [Installazione del motore di Windows PowerShell 2.0](Installing-the-Windows-PowerShell-2.0-Engine.md). Per informazioni sull'avvio del motore di Windows PowerShell 2.0, vedere [Avvio del motore di Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md)..

## Ambiente preinstallazione di Windows
Windows PowerShell 2.0, Windows PowerShell 3.0 e Windows PowerShell 4.0 eseguiti in Ambiente preinstallazione di Windows (Windows PE). I cmdlet seguenti non sono tuttavia supportati:

-   [Cmdlet di BITS (Servizio trasferimento intelligente in background)](http://go.microsoft.com/fwlink/?LinkId=257514)

-   [Get-EventLog](https://technet.microsoft.com/en-us/library/b4985b11-82bf-487d-928d-becd96fc0419)

-   [Get-WinEvent[PSITPro5_Diagnostic]](https://technet.microsoft.com/en-us/library/5fe94870-ed6b-4ce2-9500-93846cc65c95)

-   [Save-Help](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa)

-   [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545)

Inoltre, il servizio **WinRm** non è presente in Windows PE.

## Vedere anche
[Guida introduttiva a Windows PowerShell](../getting-started/Getting-Started-with-Windows-PowerShell.md)
[Installazione di Windows PowerShell](Installing-Windows-PowerShell.md)
[Avvio di Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=May16_HO2-->


