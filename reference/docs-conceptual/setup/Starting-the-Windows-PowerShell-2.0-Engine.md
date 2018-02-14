---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Avvio del motore di Windows PowerShell 2.0
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
ms.openlocfilehash: f074330953164c49d9bfaa3eb7ca1c1638eeeb76
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="starting-the-windows-powershell-20-engine"></a>Avvio del motore di Windows PowerShell 2.0

Questa sezione spiega come avviare il motore di Windows PowerShell 2.0 in Windows 8.1, Windows Server 2012 R2, Windows 8 e Windows Server 2012, che includono il motore di Windows PowerShell 2.0, e in altri sistemi in cui sono invece installati Windows PowerShell 2.0, Windows PowerShell 3.0 e Windows PowerShell 4.0.

Windows PowerShell 4.0 e Windows PowerShell 3.0 sono progettati per essere compatibili con Windows PowerShell 2.0. I cmdlet, i provider, gli snap-in, i moduli e gli script scritti per Windows PowerShell 2.0 possono essere eseguiti senza modifiche in Windows PowerShell 4.0 e Windows PowerShell 3.0. Tuttavia, a causa di una modifica nei criteri di attivazione di runtime in Microsoft .NET Framework 4, i programmi host di Windows PowerShell scritti per Windows PowerShell 2.0 e compilati con Common Language Runtime (CLR) 2.0 non possono essere eseguiti senza modifiche in Windows PowerShell 3.0 o Windows PowerShell 4.0, che sono compilati con CLR 4.0. Il motore di Windows PowerShell 2.0 deve essere usato solo quando non è possibile eseguire un programma host o uno script esistente perché non è compatibile con Windows PowerShell 4.0, Windows PowerShell 3.0 o Microsoft .NET Framework 4. È previsto che questi casi siano rari.

Molte applicazioni che richiedono l'uso del motore di Windows PowerShell 2.0 lo avviano automaticamente. Queste istruzioni sono incluse per i rari casi in cui è necessario avviare il motore manualmente.

## <a name="installing-and-enabling-required-programs"></a>Installazione e abilitazione delle applicazioni necessarie

Prima di avviare il motore di Windows PowerShell 2.0, abilitare il motore di Windows PowerShell 2.0 Engine e Microsoft .NET Framework 3.5 con Service Pack 1. Per istruzioni, vedere [Installazione di Windows PowerShell](Installing-Windows-PowerShell.md).

I sistemi in cui è installato [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) o Windows Management Framework 3.0 hanno tutti i componenti necessari. Non è richiesta alcuna configurazione aggiuntiva. Per informazioni sull'installazione di [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) o Windows Management Framework 3.0, vedere [Installazione di Windows PowerShell](Installing-Windows-PowerShell.md).

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Come avviare il motore di Windows PowerShell 2.0

Quando si avvia Windows PowerShell, per impostazione predefinita viene eseguita la versione più recente. Per avviare Windows PowerShell con il motore di Windows PowerShell 2.0, usare il parametro Version di PowerShell.exe. Si può eseguire il comando in qualsiasi prompt dei comandi, inclusi Windows PowerShell e Cmd.exe.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Come avviare una sessione remota con il motore di Windows PowerShell 2.0

Per eseguire il motore di Windows PowerShell 2.0 in una sessione remota, creare una configurazione di sessione (detta anche "endpoint") nel computer remoto che carica il motore di Windows PowerShell 2.0. La configurazione di sessione viene salvata nel computer remoto e può essere usata da qualsiasi utente autorizzato a creare sessioni che usano il motore di Windows PowerShell 2.0.

Si tratta di un'attività avanzata, che in genere viene eseguita dagli amministratori di sistema.

La procedura seguente usa il parametro **PSVersion** del cmdlet [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) per creare una configurazione di sessione che usa il motore di Windows PowerShell 2.0. Si può anche usare il parametro **PowerShellVersion** del cmdlet [New-PSSessionConfigurationFile](https://technet.microsoft.com/en-us/library/5f3e3633-6e90-479c-aea9-ba45a1954866) per creare un file di configurazione per una sessione che carica il motore di Windows PowerShell 2.0. Per modificare una configurazione di sessione in modo che usi il motore di Windows PowerShell 2.0 si può usare il parametro **PSVersion** del cmdlet [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea).

Per altre informazioni sui file di configurazione della sessione, vedere [about_Session_Configuration_Files](https://technet.microsoft.com/en-us/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Per informazioni sulle configurazioni di sessione, incluse impostazione e sicurezza, vedere [about_Session_Configurations[v4]](https://technet.microsoft.com/en-us/library/a2fbe12a-350c-4d04-be50-24102824e3ab).

#### <a name="to-start-a-remote-windows-powershell-20-session"></a>Per avviare una sessione remota di Windows PowerShell 2.0

1. Per creare una configurazione di sessione che richiede il motore di Windows PowerShell 2.0, usare il parametro **PSVersion** del cmdlet [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) impostando il valore "2.0". Eseguire questo comando nel computer che si trova sul "lato server" o ricevente della connessione.

   Il comando di esempio seguente crea la configurazione di sessione PS2 nel computer Server01. Per eseguire il comando, avviare Windows PowerShell 4.0 o Windows PowerShell 3.0 con l'opzione **Esegui come amministratore**.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. Per creare nel computer Server01 una sessione che usa la configurazione di sessione PS2, usare il parametro **ConfigurationName** dei cmdlet per la creazione di una sessione remota, ad esempio [New-PSSession](https://technet.microsoft.com/en-us/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f).

   All'avvio di una sessione che usa la configurazione di sessione, il motore di Windows PowerShell 2.0 viene caricato automaticamente.

   Il comando seguente avvia nel computer Server01 una sessione che usa la configurazione di sessione PS2. Il comando salva la sessione nella variabile $s.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Come avviare un processo in background con il motore di Windows PowerShell 2.0

Per avviare un processo in background con il motore di Windows PowerShell 2.0, usare il parametro **PSVersion** del cmdlet [Start-Job](https://technet.microsoft.com/en-us/library/2bc04935-0deb-4ec0-b856-d7290cca6442).

Il comando seguente avvia un processo in background con il motore di Windows PowerShell 2.0

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Per altre informazioni sui processi in background, vedere [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).
