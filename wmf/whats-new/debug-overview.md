---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Miglioramenti per il debug degli script di PowerShell
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855446"
---
# <a name="improvements-in-powershell-script-debugging"></a>Miglioramenti per il debug degli script di PowerShell

PowerShell 5.0 include diversi miglioramenti che ottimizzano l'esperienza di debug.

## <a name="break-all"></a>Interrompi tutto

La console di PowerShell e PowerShell ISE ora consentono di interrompere il debugger per gli script in esecuzione. Questa funzionalità è disponibile sia per le sessioni locali che remote.

Nella console premere <kbd>CTRL</kbd>+<kbd>INTERR</kbd>.

In ISE premere <kbd>CTRL</kbd>+<kbd>B</kbd> oppure usare il comando di menu **Debug -> Interrompi tutto**.

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a>Debug remoto e modifica dei file remota in PowerShell ISE

PowerShell ISE consente ora di aprire e modificare i file in una sessione remota eseguendo il comando PSEdit.
Ad esempio, è possibile aprire un file per la modifica dalla riga di comando in una sessione remota nel modo seguente:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Inoltre, è ora possibile modificare e salvare le modifiche in un file remoto che viene aperto automaticamente in PowerShell ISE quando si raggiunge un punto di interruzione. È ora possibile eseguire il debug di un file di script in esecuzione in un computer remoto, modificare il file per correggere un errore ed eseguire nuovamente lo script modificato.

## <a name="advanced-script-debugging"></a>Debug avanzato degli script

Sono disponibili nuove funzionalità di debug avanzate che consentono di collegare qualsiasi processo del computer locale che ha caricato PowerShell e di eseguire il debug di spazi di esecuzione arbitrari in tale processo.

### <a name="runspace-debugging"></a>Debug di spazi di esecuzione

Sono stati aggiunti nuovi cmdlet che consentono di elencare gli spazi di esecuzione correnti in un processo e collegare il debugger della console di PowerShell o di PowerShell ISE a tale spazio di esecuzione per il debug degli script:

- Get-Runspace
- Debug-Runspace
- Enable-RunspaceDebug
- Disable-RunspaceDebug
- Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Collegarsi a un processo che ospita PowerShell

È ora possibile collegarsi a qualsiasi processo di computer con PowerShell caricato. Per eseguire questa operazione, avviare una sessione interattiva con il processo host. Per altre informazioni, vedere:

- [Enter-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [Exit-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
