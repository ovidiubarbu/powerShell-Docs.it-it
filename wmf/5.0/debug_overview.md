---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 9ead27fd5d4f146e9062488c1c8cc22a073b922e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187103"
---
# <a name="improvements-in-powershell-script-debugging"></a>Miglioramenti per il debug degli script di PowerShell

In PowerShell 5.0 sono stati introdotti numerosi miglioramenti per ottimizzare l'esperienza di debug.

## <a name="break-all"></a>Interrompi tutto

La console di PowerShell e Windows PowerShell ISE ora consentono di interrompere il debugger per gli script in esecuzione. Questa funzionalità è disponibile sia per le sessioni locali che remote.

Nella console premere **CTRL+INTERR**.

In ISE premere **CTRL+B** oppure usare il comando di menu **Debug -> Interrompi tutto**.

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a>Debug remoto e modifica dei file remota in Windows PowerShell ISE

Windows PowerShell ISE consente ora di aprire e modificare i file in una sessione remota eseguendo il comando PSEdit.
Ad esempio, è possibile aprire un file per la modifica dalla riga di comando in una sessione remota nel modo seguente:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Inoltre, è ora possibile modificare e salvare le modifiche in un file remoto che viene aperto automaticamente in Windows PowerShell ISE quando si raggiunge un punto di interruzione.
È ora possibile eseguire il debug di un file di script in esecuzione in un computer remoto, modificare il file per correggere un errore ed eseguire nuovamente lo script modificato.

## <a name="advanced-script-debugging"></a>Debug avanzato degli script

Sono disponibili nuove funzionalità di debug avanzate che consentono di collegare qualsiasi processo del computer locale che ha caricato Windows PowerShell e di eseguire il debug di spazi di esecuzione arbitrari in tale processo.

### <a name="runspace-debugging"></a>Debug di spazi di esecuzione

Sono stati aggiunti nuovi cmdlet che consentono di elencare gli spazi di esecuzione correnti in un processo e collegare il debugger della console di Windows PowerShell o di ISE a tale spazio di esecuzione per il debug degli script:

-   Get-Runspace
-   Debug-Runspace
-   Enable-RunspaceDebug
-   Disable-RunspaceDebug
-   Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Collegarsi a un processo che ospita PowerShell

È ora possibile collegarsi a qualsiasi processo di computer con Windows PowerShell caricato. A tale scopo, si avvia una sessione interattiva con il processo, in modo analogo a come si avvia una sessione remota interattiva eseguendo il cmdlet Enter-PSSession:

-   Enter-PSHostProcess
-   Exit-PSHostProcess
