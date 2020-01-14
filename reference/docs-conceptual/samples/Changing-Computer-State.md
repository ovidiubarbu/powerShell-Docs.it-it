---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Modifica dello stato del computer
ms.openlocfilehash: 9278df55ba027134a61c8ed4e89b5b839d460b29
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736914"
---
# <a name="changing-computer-state"></a>Modifica dello stato del computer

Per reimpostare un computer in PowerShell, usare uno strumento da riga di comando standard o una classe WMI o CIM.
Anche se si usa PowerShell solo per eseguire lo strumento, imparare a modificare lo stato di alimentazione di un computer in PowerShell aiuta a scoprire alcuni importanti dettagli relativi all'uso di strumenti esterni in PowerShell.

## <a name="locking-a-computer"></a>Blocco di un computer

L'unico modo per bloccare un computer direttamente con gli strumenti disponibili standard consiste nel chiamare la funzione **LockWorkstation ()** in **user32. dll**:

```powershell
rundll32.exe user32.dll,LockWorkStation
```

Questo comando blocca immediatamente la workstation. Usa **rundll32.exe**, che esegue le DLL di Windows (e salva le relative librerie per poterle usare più volte) per eseguire `user32.dll`, una libreria di funzioni di gestione di Windows.

Quando si blocca una workstation mentre è abilitata la funzionalità Cambio rapido utente, ad esempio in Windows XP, il computer visualizza la schermata di accesso utente invece dello screen saver dell'utente corrente.

Per arrestare una sessione specifica in Terminal Server, usare lo strumento da riga di comando **tsshutdn.exe**.

## <a name="logging-off-the-current-session"></a>Disconnessione dalla sessione corrente

È possibile usare alcune tecniche diverse per disconnettersi da una sessione nel sistema locale. Il modo più semplice è l'uso dello strumento da riga di comando di Desktop remoto/Servizi terminal, **logoff.exe**. Per i dettagli, al prompt di PowerShell digitare `logoff /?`. Per disconnettere la sessione attiva corrente, digitare `logoff` senza argomenti.

È anche possibile usare lo strumento **shutdown.exe** con la relativa opzione di disconnessione:

```powershell
shutdown.exe -l
```

Un'altra opzione prevede l'uso di WMI. La classe **Win32_OperatingSystem** include un metodo **Shutdown**.
È possibile richiamare il metodo con il contrassegno 0 per avviare la disconnessione:

Per altre informazioni sul metodo **Shutdown**, vedere [Metodo Shutdown della classe Win32_OperatingSystem](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a>Arresto o riavvio di un computer

L'arresto e il riavvio dei computer sono in genere gli stessi tipi di attività. Gli strumenti per l'arresto di un computer di solito consentono anche di riavviarlo e viceversa. Sono disponibili due opzioni semplici per riavviare un computer da PowerShell. Usare **tsshutdn.exe** o **shutdown.exe** con gli argomenti appropriati. È possibile ottenere informazioni di utilizzo dettagliate da `tsshutdn.exe /?` o `shutdown.exe /?`.

È anche possibile eseguire operazioni di arresto e riavvio direttamente da PowerShell.

Per arrestare il computer, usare il comando Stop-Computer

```powershell
Stop-Computer
```

Per riavviare il sistema operativo, usare il comando Restart-Computer

```powershell
Restart-Computer
```

Per forzare il riavvio immediato del computer, usare il parametro -Force.

```powershell
Restart-Computer -Force
```
