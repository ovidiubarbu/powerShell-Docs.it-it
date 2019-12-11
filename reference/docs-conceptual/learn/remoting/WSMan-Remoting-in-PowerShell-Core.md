---
title: Comunicazione remota di WS-Management (WS-Management) in PowerShell Core
description: Comunicazione remota in PowerShell Core tramite WSMan
ms.date: 08/06/2018
ms.openlocfilehash: e5f00128bc8ebc1b432cc77a5896a9e09d684109
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "62058880"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a>Comunicazione remota di WS-Management (WS-Management) in PowerShell Core

## <a name="instructions-to-create-a-remoting-endpoint"></a>Istruzioni per creare un endpoint di comunicazione remota

Il pacchetto PowerShell Core per Windows include un plug-in WinRM (`pwrshplugin.dll`) e uno script di installazione (`Install-PowerShellRemoting.ps1`) in `$PSHome`.
Questi file consentono a PowerShell di accettare le connessioni remote PowerShell in ingresso quando viene specificato l'endpoint.

### <a name="motivation"></a>Motivazione

Un'installazione di PowerShell può stabilire sessioni di PowerShell con i computer remoti usando `New-PSSession` e `Enter-PSSession`.
Per abilitarla ad accettare le connessioni remote PowerShell in ingresso, l'utente deve creare un endpoint di comunicazione remota WinRM.
Si tratta di uno scenario di consenso esplicito in cui l'utente esegue Install-PowerShellRemoting.ps1 per creare l'endpoint WinRM.
Lo script di installazione è una soluzione provvisoria fino a quando non verranno aggiunte altre funzionalità a `Enable-PSRemoting` per eseguire la stessa azione.
Per altri dettagli, vedere il problema [n. 1193](https://github.com/PowerShell/PowerShell/issues/1193).

### <a name="script-actions"></a>Azioni dello script

Lo script

1. Crea una directory per il plug-in all'interno di `$env:windir\System32\PowerShell`
1. Copia pwrshplugin.dll in questo percorso
1. Genera un file di configurazione
1. Registra il plug-in in WinRM

### <a name="registration"></a>Registrazione

Lo script deve essere eseguito all'interno di una sessione di PowerShell a livello di amministratore e viene eseguito in due modalità.

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>Eseguito dall'istanza di PowerShell che verrà registrata

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>Eseguito da un'altra istanza di PowerShell per conto dell'istanza che verrà registrata

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

Ad esempio:

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

**NOTA**: lo script di registrazione della comunicazione remota riavvierà WinRM, in modo che tutte le sessioni PSRP esistenti vengano terminate subito dopo l'esecuzione dello script. Se eseguito durante una sessione remota, la connessione viene interrotta.

## <a name="how-to-connect-to-the-new-endpoint"></a>Come connettersi al nuovo endpoint

Stabilire una sessione di PowerShell con il nuovo endpoint PowerShell specificando `-ConfigurationName "some endpoint name"`. Per connettersi all'istanza di PowerShell dall'esempio precedente, usare una delle chiamate seguenti:

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

Si noti che le chiamate `New-PSSession` e `Enter-PSSession` in cui non viene specificato `-ConfigurationName` avranno come destinazione l'endpoint PowerShell predefinito, `microsoft.powershell`.